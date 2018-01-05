---
title: "Data analysis on the go"
date: 2015-03-22T17:30:00-05:00
tags: 
  - data
---

A recent [Fast Company article][tableau] describes Tableau's latest app, [Project Elastic][elastic], as a potential game-changer in mobile data analysis. The app would allow iPad users to move from an Excel file in Mail.app to an interactive chart with a few quick taps. Filters can be applied/removed with swipes, zoom levels are adjusted by pinch/spread gestures, and charts can be shared via email.

It's a cleverly designed interface, but Elastic suffers from a critical problem: it assumes the user is accessing clean datasets. 

Contrary to [popular belief][datasexy], the real work of a data scientist isn't sexy. A large chunk, if not a majority, of a data scientist's time is typically spent [cleaning messy data][dataclean]. By encouraging users to jump straight from an email attachment to data exploration, Elastic can lead to [garbage-in, garbage-out][gigo] analyses. This risk is only compounded by the targeting of the app to casual analysts. 

Elastic is an admirable effort by Tableau to bring data analysis to the iPad, but it will encourage a flawed approach to data analysis. To paraphrase Jeff Leek, [good data science may look easy, but so does bad data science][goodscience]. Elastic looks cool, but the appealing interface is a mask for an insufficiently rigorous approach to data analysis.


I have serious doubts that quality data analysis can be performed from a tablet or mobile platform. 

When asked about the potential for the iPad replacing the PC, [Steve Jobs compared it to the replacement of trucks by cars][trucks]: 

>“When we were an agrarian nation, all cars were trucks, because that’s what you needed on the farm. But as vehicles started to be used in the urban centers, cars got more popular. Innovations like automatic transmission and power steering and things that you didn’t care about in a truck as much started to become paramount in cars. … PCs are going to be like trucks. They’re still going to be around, they’re still going to have a lot of value, but they’re going to be used by one out of X people. … I think that we’re embarked on that. 

Mobile computing is replacing PC's for millions of people around the globe for tasks like email, photography, personal finance, and gaming, but there are still many jobs that ought not be done on a mobile device.  Attempting to move data analysis to the iPad makes about as much sense as trying to move a piano with a Prius - just because it's possible, doesn't mean it should be done. 

Bottom line: if someone emails you a spreadsheet, you should probably wait to get to a PC before attempting to dig in to the data. 

[tableau]: http://www.fastcompany.com/3042357/tableau-elastic-tinder-like-data-visualization

[elastic]: http://www.tableau.com/be-elastic

[datasexy]: https://hbr.org/2012/10/data-scientist-the-sexiest-job-of-the-21st-century/

[dataclean]: http://www.nytimes.com/2014/08/18/technology/for-big-data-scientists-hurdle-to-insights-is-janitor-work.html?_r=1

[goodscience]: http://simplystatistics.org/2015/03/17/data-science-done-well-looks-easy-and-that-is-a-big-problem-for-data-scientists/

[gigo]: https://en.wikipedia.org/wiki/Garbage_in,_garbage_out

[trucks]: http://allthingsd.com/20100601/steve-jobs-session/