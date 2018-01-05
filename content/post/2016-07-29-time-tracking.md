---
title: Time Tracking
date: 2016-07-29T20:49:00-05:00
tags: 
  - R
  - podcast
  - productivity
---

I tweeted this out earlier today: 

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">Insights from time tracking: I need to do more <a href="https://twitter.com/hashtag/rstats?src=hash">#rstats</a> programming on Thursday/Friday afternoons. Also, mtgs suck. <a href="https://t.co/14dFtGNubP">pic.twitter.com/14dFtGNubP</a></p>&mdash; Alex Spurrier (@alspur) <a href="https://twitter.com/alspur/status/759097342435917824">July 29, 2016</a></blockquote> <script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

Why do I have time tracking charts that break down when I do certain kinds of work? 

A book ([Deep Work][deepwork]) and a podcast ([Cortex][cortex]).

I know that the ability to focus is important to the work I do, but [Deep Work][deepwork] by Cal Newport helped articulate precisely *why* it's extremely important to cultivate the ability to perform "deep work." I recommend reading the book, but the tl;dr is that in order to succeed in today's economy, one needs to be able to perform extremely cognitively demanding work with speed and quality. In order to accomplish that kind of work, one needs to be able to "focus intently without distraction."

The constant stream of email, texts, meetings, and phone calls that are commonplace in modern offices help keep us informed and connected to our coworkers, but it often prevents us from being able to maintain sustained periods of focus on cognitively demanding tasks. Newport makes several recommendations to combat distraction, but I found the most helpful advice was to schedule every minute of my day. 

The purpose of scheduling every minute of your day isn't to hold yourself to an itinerary without any allowance for deviations. Instead, it's a way to be more intentional about how you're spending your time. More importantly, it can help you better track the amount of deep work you're actually accomplishing.

I currently use my calendar as a guide for how I'm going to spend my week. There are always meetings I have to work around, but every other minute at work is allocated to a specific type of work. Despite my best intentions, reality doesn't always align with the calendar I set, so I needed another system to help me better track the work I actually accomplish.

Enter [Cortex][cortex]. 

Cortex is a podcast featuring [Myke Hurley](http://www.twitter.com/imyke) and [C.G.P. Grey](http://www.twitter.com/cgpgrey) talking about how they get their work done. In their third episode, [Grey reveals](cortex3lcp) that he uses [Launch Center Pro][lcp] and [Due][due] as a time tracking system. The workflow goes something like this:

- Start a 40 minute timer in Due & begin working
- When the timer goes off, open Launch Center Pro, which has several actions associated with a specific type of work you do
- Trigger the action associated with the work you just performed, which adds a row to a spreadsheet detailing the time and type of work you're doing.
- Reset timer and continue working.

Like any good nerd, I've tweaked this system a little. I've integrated [Drafts][drafts] actions with the Launch Center Pro actions so I can capture a little more context about the work I'm doing. I also use [R Markdown][rmd] to convert the spreadsheet of my time tracking data into charts in a PDF that help me understand how I'm spending my time.

This took a little bit of work to set up, but it's been extremely helpful. Every Friday afternoon, I look at the PDF produced by the R Markdown script I wrote a few months ago. It's helped me realize how productive I am before 9am. I now make sure that before I leave the office, I'm clear on the work I want to tackle the first thing the following morning. Conversely, looking at the data also shows me I still have to work on making the afternoons on Thursdays and Fridays more productive.  

If you're interested in improving your capacity for deep work, start with tracking your time.

[rmd]: http://rmarkdown.rstudio.com/

[deepwork]: https://itun.es/us/mqIh7.l

[cortex]: http://relay.fm/cortex

[cortex3lcp]: https://overcast.fm/+EtBmIVZeo/1:02:17

[lcp]: https://appsto.re/us/gSEQV.i

[due]: https://appsto.re/us/XoZpx.i

[drafts]: https://appsto.re/us/BTL91.i