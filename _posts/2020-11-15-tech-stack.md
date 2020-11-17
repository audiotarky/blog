---
layout: post
title:  Tech stack
categories: technology
tags:
  - python
  - analytics
  - web-monetisation
  - transparency
excerpt: How Audiotarky works.
author: Simon
---

> Buy it, use it, break it, fix it, trash it, change it, mail, upgrade it

While we're still very much "in development" I thought it might be interesting to write up the tech stack that's in use today, if only as a historical record to compare back to in the future.

The site uses [Flask][flask] in the backend, and [Jekyll][jekyll] to render static content. For the initial phase of development, we're avoiding databases in the backend - the content is not that dynamic, in fact its almost write once. Jekyll means we can pre-render the pages, apply changes to templates etc. easily. There are a few "interesting" templates that are being built, and that probably points to Jekyll not being a long term solution ([Hugo](https://gohugo.io/) looks interesting).

We've so far avoided a front end framework, though I expect that will be changing soon. That said, I'd like to keep any UI framework minimal, & standards based.

We're trying to be privacy concious, and the architecture & use of [Coil][coil] means we _need_ to know very little about our audience, but also do want to understand _some_ of what people are doing. To that end we've got [Fathom][fathom]* providing some "non-creepy" analytics.

The flask app is hosted on [PythonAnywhere][pythonanywhere]* which I stumbled upon, and have so far been very impressed with. There's some work to do to better use their service (static assets, some scheduled tasks, maybe some further deployment automation) but for now it's doing whats needed. It's simple, it does what you need & gets out the way - winner!

The flask app is used to change how audio is served based on whether the listener has [Coil][coil] enabled. To do this we're using [Vanilla][vanilla] to verify a payment stream, and some code that will be open sourced in the future.

Last there are some google forms/sheets & associated python scripts to pull data. These are used for [expression of interest][eoi] & artist sign up


<p class="small">* referal link</p>
[fathom]: https://usefathom.com/ref/KP7MDR
[flask]: https://flask.palletsprojects.com/en/1.1.x/
[pythonanywhere]: https://www.pythonanywhere.com/?affiliate_id=0086ceb1
[jekyll]: https://jekyllrb.com/
[vanilla]: https://admin.vanilla.so/
[coil]: https://coil.com
[eoi]: https://forms.gle/7irCZKrSUaZjRnZk7