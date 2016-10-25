---
layout:        post
title:         "AAS Divison of Planetary Science Conference"
subtitle:      "Announcing the start of a consolidated planetary science Python package."
authors:       michaelaye
header-img:    "img/post-bg-05.jpg"
category:      Community
tags:          [Python, SPICE, Story telling]
slack_channel: planetarypy
---

## Conferencing

Wow, this was a busy conference. Once per year the "Division for Planetary Science" (DPS) of
the American Astronomical Society meets to present and discuss the most recent results.
This time, it was even a joined conference with its European pendent the EPSC conference, which meant that I met even many more known faces than usual on a US conference (with me being German). The meeting location was the lovely Pasadena, CA.

I was travelling there on the account of my work on Saturn's rings,
presenting a poster about a [solitary wave traveling through
the rings](http://adsabs.harvard.edu/abs/2016DPS....4812103A).
But I also presented a poster about [the OpenPlanetary initiative](http://adsabs.harvard.edu/abs/2016DPS....4841908M).

During the session for the OpenPlanetary poster, I was visited by
[Geert Barentsen](http://twitter.com/GeertHub), a K2 astronomer and
[Gus Muench](http://twitter.com/augustmuench), an astromoner and data scientist that now
works for [AAS publishing](http://twitter.com/AAS_Publishing).
We had a very nice long chat about bridging the gap between publications and the precise set
of data used for creating them.
Gus also chatted with the maintainers of the [Planetary Data System](https://pds.nasa.gov),
to find out how to enable such deep linking into the current storage archives for
planetary data.
It does not seem possible yet, but I'm glad that some people talk about these important steps
for improving the reproducability of published work.

## SPICE updates

Ever since I had my first course on [SPICE](http://naif.jpl.nasa.gov/naif/), a computational
toolset for geometry calculations in the solar system, I always say hello to the lead of
the project, Chuck Acton. SPICE is so essential to today's operation of spacecraft and the precise analysis of data from them, that I consider it my responsibility to not only update myself about the current status, but also keep an ear open for any hurdles that Chuck has to overcome in his everyday job.

Because it just happens to be the case, that for years, this essential service was, IMHO, vastly under-appreciated by the powers that be, and I made sure to carry on and spread any new miseries that were stopping SPICE from becoming as good as it should be. I'm not sure if I ever helped really by spreading the noise, but at least I tried.

I'm happy to report that after an official review of their service in the beginning of 2016, the group finally was allowed to [hire 1.75 additional permanent staff](http://openplanetary.co/blog/community/JPL-NAIF-SPICE-Employment-Opportunity.html), which most likely means that we finally will see an official Python version from them, although I have to say, [SpiceyPy](https://github.com/AndrewAnnex/SpiceyPy) works already very fine.

## ... to boldly go ...

Which brings me to my last exciting point I'd like to make about the conference.
[Erik Tollerud](http://twitter.com/eteq) presented the well-used [astropy](http://www.astropy.org) community python library for astronomy on a workshop on Monday and started discussions about how nice it would be to have something similar for planetary science.

Now, I am brooding over this point for several years already, and I am sharing this itch with a few other characters on github, e.g. [Austin Godber](https://github.com/godber) and [Trevor Olson](https://github.com/wtolson), who implemented some really helpful pieces of code for working with PDS and [ISIS](https://isis.astrogeology.usgs.gov) data files, and working with the label files. These tools are currently _resting_ [here](https://github.com/planetarypy) under the umbrella organisation **PlanetaryPy**.
Just recently we were discussing to create another module for general PDS tools, as there are several activities, like parsing the labels to get the column names for a cumulative index files for PDS data, reading that file and transforming it into a modern data table like a _pandas_ Dataframe... this most likely is being done over and over again by other PDS users.

Additionally, even before PlanetaryPy was a thing, I implemented a web-scraper for planetary body constants and put them into a module called **planetpy** [here](https://github.com/michaelaye/planetpy) (plus a few more tools).
And there's several space instrument data readers I finally should publish, and those GIS related image analysis tools... _waaah_ ;)

On the last day at the conference, I had a brilliant 90 minute chat with Erik and while, at first, we just leisurely talked about how nice it would be to have a planetarypy package, he understood (I think) that I (and others) are quite serious about this, and he motivated me with some ideas on how to proceed.

### The beginning...

So, long story short, it's about time to let us unite all these Python tools that are flying around, and come up with a stable and well-tested Python package with a well-defined API.
As you can imagine, good APIs don't fall out of the sky, so it will be an uphill battle, but after a call to action I already made on our general Slack channel of the OpenPlanetary project, 21 people have joined a new channel (linked below) focusing on the next steps to make this happen.

One of the first steps, that I agreed with Erik will be immensely useful, is to create a requirements and status document that identifies potential overlap with the astropy package. This will prevent re-inventing the wheel and Erik is quite willing to discuss, using such a document as an interface, where `planetarypy` (the community) and `planetpy` (just my first idea on names, historically grown ;) ) have an overlap and maybe astropy could be slightly boosted to supported certain tasks, but also to see where things are cleary so special that there is no room within the astropy package to support it.

To flesh this out, I will start tomorrow the discussions on our Slack portal at the channel _planetarypy_ that is linked below. Join us, if you would like to participate.

> Forward. Never backwards.
