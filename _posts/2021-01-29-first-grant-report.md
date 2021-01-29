---
layout: post
title: "Diverse income streams for musicians via web monetisation — Grant Report #1"
categories: transparency
tags:
  - "grant for the web"
  - transparency
excerpt: Our mid-period grant report
author: Simon
---

_Reblogged from [the Web Monetization community](https://community.webmonetization.org/drsm79/diverse-income-streams-for-musicians-via-web-monetisation-grant-report-1-4mc9)_

## Image

![Audiotarky](https://www.audiotarky.com/$/images/audiotarky_logo_v1@2x.png)

## Project Update

The project is launching under the brand [Audiotarky][beta], and is currently in a private beta (we're letting people know about the site, but the [root URL is still a placeholder][audiotarky]).

Like so many others, we have definitely seen the impact of covid on planned work - making certain things we'd planned to do take longer or not be possible (see below). Two team members have changed jobs and one has become a grandad during the project. Life, finds a way.

![Life, finds a way.](https://media3.giphy.com/media/VHW0X0GEQQjiU/giphy.gif)

We've open sourced some of the underlying code, and have some more components to release in the coming months.

## Progress on objectives

We have built a site that facilitates musicians getting directly paid through web monetisation. This has some nice benefits for the listeners too; we can serve them great music without needing to know anything about them. We don't need to track their habits, or even know who they are - if they have a WM enabled browser they can listen to music & pay the people who made it. We're in beta currently, but should be publicly available in the next month.

Pulling together the various pieces is nearly complete, the project is now switching to one of promotion, open sourcing components & writing up what we've done & what has been learned along the way.

## Key activities

The site has launched as a [private beta][beta]. We are working on signing up more artists as I type, and expect to make the site publicly available by end of Feburary. We've focussed on the "consumer" end of the application - letting people listen to music, monetised via WM, in a privacy centric manner.

On reflection the idea of "scraps" doesn't fit WM so well, as scraps are less "engaging" (you'd download the pieces in seconds and play/use them offline) but is good for more general micropayment models. I plan to add a simple version of this to the site post-launch, but would be interested in ideas for how others have done micropayment (as opposed to streamed payments) or addressed offline use cases. One approach would be a VST or other such plugin which streamed payment as people used the scraps, but this would be a substantial piece of development.

We've been documenting progress and deliverables approx. monthly on [our blog][blog]. We have posts on how the T&Cs work & how the brand developed planned, as well as a few "how we've done X" type of posts and a short update on the tech stack used.

We've open sourced a [key piece of the technology stack][wm-flask] in (and [announced here][verify-announce]). This lets others build payment verification into their applications more easily.

We have done the first 2 days of recording, with 6 tracks laid down, and have 4 more scheduled in Feburary. Mastering it should be relatively quick, and this should complete the album in March.

Covid lockdowns have made scheduling these sessions more difficult (lots of moving parts). The original idea was to have these recordings as the first "proof point" content on the site, and to have a videographer document the sessions to be used as content marketing for the project.

Given the lockdowns in the UK, the videographer became impractical and we've had delays getting into the studio, so we've shifted to getting more musicians involved (see next section), and filed for a budget reallocation to redirect funds accordingly. This hopefully gives us sufficient data to prove the model (or otherwise). I plan to make said data public, and keep it current after the grant period as part of the transparency efforts around Audiotarky itself.

## Communications and marketing

As mentioned above, covid lockdowns have delayed recording sessions for the planned album, and made professionally documenting those recording sessions impractical, so we've switched tack and redirected budget to help promote to other artists. Part of this redirected budget will be used to bolster the planned reward payments to creators. The remainder will be used to pay for a marketing consultant to initially help get artists (we're aiming for ~50 in the next month or two) signed up to the site, and then encourage users to come listen!

## What’s next?

What remains?

- doing the other parts of my grant report!
- completing the album, releasing it under Creative Commons through Audiotarky
- signing up more artists & responding to feedback from the beta program
- starting to collect and publish data about usage & payment
- start the data pipeline for reporting on the platform long term
- further blogs on how the site works

I'd hoped to have a decently sized "data set" by the end of the grant, but I think we'll be only have a month or so of data. I think for a site like [Audiotarky][audiotarky] its important to make much of this data public, and plan to have it collected & presented automatically into the future. I'd be interested to know whether this would be worth getting a grant extension for, or not.

## What community support would benefit your project?

Feedback on the pieces we've opened sourced would be very welcome, as would patches/bug reports/improvement suggestions.

General advice/ideas on how to encourage people not familiar with WM to use it (as either a creator or consumer) would be very welcome - I think this echoes comments on a few other reports. There seems to be a gap in the market to allow someone to send modest amounts of money to an ILP, without the need of a third party tool - maybe something to look at in future grants?

We'd be really keen to see more artists come our way, and for folk to come listen :) Feedback (and forgiveness as we iterate!) as comments on this post would be amazing. Really interested to compare notes with others doing work in the WM/Music space, too.

## Additional comments

Registering with the IRS was an unexpected ... joy, and one that would be useful to highlight for future grant rounds (at least to people like me!)

## Relevant links/resources  (optional)

[Private beta][beta]
[WM verification flask server][wm-flask]

[audiotarky]: https://audiotarky.com
[beta]: https://audiotarky.com/$/
[blog]: https://blog.audiotarky.com
[wm-flask]: https://github.com/audiotarky/wm-flask
[verify-announce]: https://community.webmonetization.org/drsm79/payment-verification-fdj