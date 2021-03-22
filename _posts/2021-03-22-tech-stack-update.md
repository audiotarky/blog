---
layout: post
title: Tech stack update
categories: technology
tags:
  - python
  - analytics
  - web-monetisation
  - transparency
excerpt: How Audiotarky works now.
author: Simon
---

Now the site is "launched" I thought it would be worth revising [the blog from November]([2020-11-15-tech-stack](https://blog.audiotarky.com/2020/11/15/tech-stack/index.html)) & see whats changed, whats stayed the same.

The site is still hosted on [Python Anywhere][pythonanywhere]*, which has been a very reliable and fully featured service. The one thing that has been a very mild hassle was needing a third party to support naked domains. Luckily [NakedSSL][nakedssl] are hassle free, and a nice "just works" tool. The one big change in the backend is switching to the [WebMonetization.org payment verifier][wm-verify]. There was nothing wrong with [vanilla][], but I was hoping changing would address a bug with Puma browser, and the API is slightly cleaner for the wm.org one. The bug, annoyingly, remains.

We're still using [Fathom][fathom]* for "non-creepy" analytics. It's been useful for that, but I need to spend some more time with it to get the most out of it (for e.g. adding some more goals). We're also using Fathom for status monitoring, which has been very helpful. One thing to note there, the configuration of the alerting isn't as intuitive as the rest of the service, but I think they are going to be improving that.

The big change has been in the front end & content management. The front end uses [picoapp][picoapp] & [operator][operator] to provide the "Single Page Application". Pico has been a very nice lightweight framework, and I'm glad we're using it. Adding new components is generally a breeze, and we'd not have half of the features we have without it. We're using [Tailwind][] for styling, and the excellent [AmplitudeJS][] for playing audio.

Content management is now fully [Hugo][]. It's been ideal for the site. Not only does it allow for richer queries on data (for example, "get all albums where the artist genre is hip hop") it also lets us do image processing. This has been super handy; it means we can take a large image (say a press shot) and easily scale it for use, minimising data served/transferred, and use it to make the blurred header images on each page. We're also starting on internationalisation (and have started a tool to help with that called [babelize][]).

Whats next? Well, the next big feature to add is enabling logging in with a Coil account. This should mean people can stream payments from browsers that don't have the [Coil][coil] plugin installed (e.g. Safari). That means fattening up the back end bit to support the oAuth handshake between the two sites. I'd also like to improve the streaming server - I think Safari expects [content range][content-range] to be supported for large files, and it seems it can cause some issues with scrubbing audio etc.

<p class="small">* referal link</p>

[fathom]: https://usefathom.com/ref/KP7MDR
[flask]: https://flask.palletsprojects.com/en/1.1.x/
[pythonanywhere]: https://www.pythonanywhere.com/?affiliate_id=0086ceb1
[jekyll]: https://jekyllrb.com/
[vanilla]: https://admin.vanilla.so/
[wm-verify]: https://webmonetization.org/docs/receipt-verifier
[coil]: https://coil.com
[eoi]: https://forms.gle/7irCZKrSUaZjRnZk7
[nakedssl]: https://www.nakedssl.com/
[babelize]: https://github.com/audiotarky/babelize
[picoapp]: https://github.com/estrattonbailey/picoapp
[operator]: https://github.com/estrattonbailey/operator
[Tailwind]: https://tailwindcss.com/
[AmplitudeJS]: https://521dimensions.com/open-source/amplitudejs/
[Hugo]: https://gohugo.io
[content-range]: https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Range
