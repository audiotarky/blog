---
layout: post
title: "Payment verification with Vanilla & Flask"
categories: technology
tags:
  - python
  - web-monetisation
excerpt: How we change content based on streaming payments.
author: Simon
---

Audiotarky wants to get musicians paid fairly for the music they produce.
We're using [Web Monetisation][] to power that, but there's a gap that needs
to be closed. The [exclusive content][] example is doing its magic client side
(in the browser) this makes it easily circumvented. Possibly not a big deal in
many cases, but for a music platform not really sufficient. Imagine 2 years
worth of work trivially downloaded without payment, you'd not be a happy bunny.

Fortunately the bright folk from [Cinnamon][] have already hit this problem,
and solved it via a service called [Vanilla][]. This gives you a proxy payment
pointer which the service can then verify payment on. You can then call their
API to confirm that the client has streamed payment to the site.

For Audiotarky we're using this to make a session, which our [Flask][] server
can then "see" and return the exclusive content to those who are streaming
payment to the artist.

Lets look at the code for our proving function first. This is what calls the
Vanilla API.

{% raw %}
```python
def prove(request):
    """Prove that a WM payment has occurred."""
    try:
        request_id = request.data.decode('utf-8')

        query = f'''{{
        proof(requestId: "{request_id}") {{
            total
            rate
            metadata{{
            requestId
            clientId
            contentId
            }}
        }}
    }}'''
        response = requests.post(
            CONFIG['server']['APIURL'],
            json={'query': query},
            headers={
                'Content-Type': 'application/json',
            },
            auth=HTTPBasicAuth(CONFIG['server']['ID'], CONFIG['server']['SECRET'])
        )

        response.raise_for_status()
        proof = response.json()
        if proof['data']['proof']['metadata']:
            return proof['data']['proof']
    except Exception as e:
        print(e)
    return False
```
{% endraw %}

There's nothing fantastically interesting in there, and it's essentially a
port of one of the Vanilla examples from Javasript to Python.

We now need some frontend code to create the session. Normally this would be
done when someone logs on to the site, but we're deliberately trying to avoid
such things; we're trying to be privacy focussed, after all. As the session is
only needed for visitors who are streaming payment, we can do something like
the following to create it:

```javascript
loaded = false;
if (document.monetization) {
    document.monetization.addEventListener('monetizationprogress', ({ detail }) => {
        if (!loaded) {
            loaded = true
            requestId = detail.requestId
            console.log(detail)
            var authz = new Request('/session', { method: 'POST', body: requestId });
            fetch(authz)
        }
    })
}
```

This does the following:

1. looks for whether the webmonetisation plug in is available (`if (document.monetization)`)
2. if it is, sets up a listener for when payment is streamed
3. once a payment is streamed, send the `requestId` of that payment to the `/session`
   endpoint for validation with Vanilla

`loaded` is used to track whether this has been done already, really the even
listener should be removed or similar.

The `/session` endpoint is pretty minimal, using the `prove` function from
earlier:

```python
@app.route('/session', methods=['POST'])
def make_session():
    """Create a session if the client iw WM enabled."""
    proof = prove(request)
    if proof:
        session['clientId'] = proof['metadata']['clientId']
        return 'session created'
    else:
        raise PaymentRequired()
```

OK, so we now have code that creates a session when the user is streaming
payment, great!

But... now what?

Well, now we can check that session (the session token will be sent by the
browser on each request) and decide whether "exclusive content" should be
served or not. This can be checked in the Flask app by calling

```python
session.get('clientId', False))
```

If the session exists, and is valid, the application can assume (and it is an
assumption - more later) that payment is streaming.

In the case of Audiotarky, we want musicians to be able to decide if folk can
listen to their music regardless of whether they're being paid, or that they
want to lock it down to only those who are streaming payment. At the same time,
Audiotarky itself only generates revenue if people are browsing for music &
streaming payment as they do so, so we want to encourage people to sign up to
[Coil][]. At the moment this is done visually, and also by inserting a robotic
voice (thanks to `say`) mentioning that a Coil subscription would mean people
got paid.

The plan is to bundle some of this up into [a library][] for people to use in
their own applications, but that will have to wait a little while as we build
out the site, prove the idea some more, and, most importantly, get musicians
on boarded & getting paid!

[Web Monetisation]: https://webmonetization.org/
[exclusive content]: https://webmonetization.org/docs/exclusive-content
[Vanilla]: https://vanilla.so/
[Cinnamon]: https://cinnamon.video/
[Flask]: https://flask.palletsprojects.com/en/1.1.x/
[Coil]: https://coil.com/
[a library]: https://github.com/audiotarky/wm-flask
