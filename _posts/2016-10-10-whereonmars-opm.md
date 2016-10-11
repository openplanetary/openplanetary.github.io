---
layout:     post
title:      '"Where On Mars?" Interactive Map'
subtitle:   "Building blocks of an Open Planetary Mapping platform for Researchers, Educators, and the General Public"
description:   "Building blocks of an Open Planetary Mapping platform for Researchers, Educators, and the General Public"
author:     nmanaud
header-img: img/nmanaud/wom-opm-header.jpg
category: Community
tags: [Mars, Interactive Map, Open Data, Dataviz, Story telling]
slack_channel: whereonmars-opm
image: /img/nmanaud/wom-opm-webintent.png
---

## HOW IT STARTED

*"Where On Mars?"* started off early 2015 at the European Space Astronomy Centre (ESAC) in Madrid (Spain) as a trainee project with [**Oriol Boix**](https://twitter.com/oriolbx), in collaboration with the [CARTO](https://carto.com) team: [**Carla Iriberri**](https://twitter.com/iriberri1) and [**Andrew Hill**](https://twitter.com/andrewxhill), and with the support from planetary scientists: [Peter Grindrod](https://twitter.com/Peter_Grindrod) (UK NASA RPIF/UCL) and Ernst Hauber (DLR/Berlin).

I came up with the idea while I was working as Archive Scientist for the ESA's Mars Express and ExoMars 2016 missions. The initial goal was to help increase public awareness of the ExoMars 2020 Rover mission, while experimenting with the use of modern open-source web mapping technologies applied to planetary science data and geospatial information.

### The Interactive Map

The "Where On Mars?" [interactive map](http://whereonmars.co/app) was designed as a *storymap* guiding people through the main scientific and engineering constraints for the selection of the ExoMars 2020 rover landing site. It lets you explore Mars and each candidate landing site. Here is a couple of screenshots showing you the interface:

[![Screenshot](/img/nmanaud/wom-screenshot-1.png "ExoMars LS Geological Constraints")](http://whereonmars.co/app#3)

[![Screenshot](/img/nmanaud/wom-screenshot-2.png "ExoMars Oxia Planum LS")](http://whereonmars.co/app#5)

[![Screenshot](/img/nmanaud/wom-screenshot-3.png "ExoMars Aram Dorsum LS")](http://whereonmars.co/app#7)

The interface was built as simple javascript client relying on the [CARTO Engine](https://carto.com/engine/) and other open-source mapping technologies for processing, storing, and visualising data on the web: GDAL, Leaflet, etc...

The source code of the front-end web interface is available on [GitHub](https://github.com/openplanetary/whereonmars).



### It comes with the data!

The interface visualises a selection of the same ESA and NASA's planetary satellite images, and additional geospatial information used by the scientists involved in the selection process.

<div>
  <img src="http://whereonmars.co/img/basemaps/1.png" width="24%" style="padding:4px; border-radius: 5%; display:inline-block;">
  <img src="http://whereonmars.co/img/basemaps/2.png" width="24%" style="padding:4px; border-radius: 5%; display:inline-block;">
  <img src="http://whereonmars.co/img/basemaps/3.png" width="24%" style="padding:4px; border-radius: 5%; display:inline-block;">
  <img src="http://whereonmars.co/img/basemaps/4.png" width="24%" style="padding:4px; border-radius: 5%; display:inline-block;">
</div>

Open source and collaborative from the start, we made these data available to the public through new [**Mars basemaps**](https://github.com/openplanetary/whereonmars/wiki/Basemaps) and [**geospatial data sets**](https://github.com/openplanetary/whereonmars/wiki/CartoDB-Datasets) that can be used to create new map visualisations using the [CARTO Builder](https://carto.com/builder/), or in your web mapping applications.

### Who's using it?

The project and interactive map was first presented and introduced at the [2015 European Planetary Science Conference](https://youtu.be/xps8nQwxM14) in Nantes (France) by myself, and featured at the [2015 Visualised Conference](https://vimeo.com/156503185) in New York (USA) by [Aurelia Moser](https://twitter.com/auremoser), and at the [2015 ESA's EO Open Science Conference](http://www.esa.int/spaceinvideos/Videos/2015/10/Scientific_Communication_and_Visualization) in Rome (Italy) by [Javier de la Torre](https://twitter.com/jatorre). It was also used on the [ESA's Robotic Exploration of Mars website](http://exploration.esa.int/mars/56622-exomars-2018-landing-site-search-to-narrow/) around the time of the 3rd ExoMars Rover landing site selection workshop.

Thanks to all the initiatives above, and our [@whereonmars](https://twitter.com/whereonmars) Twitter handle, we managed to engage with ~**3500 users** in the last year; with an average of ~67 users per week, and 17.8% returning users.

<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">. <a href="https://twitter.com/whereonmars">@whereonmars</a> site looking great on my extra wide-screen monitor. Very useful! <a href="https://t.co/i2cDk2QvDp">pic.twitter.com/i2cDk2QvDp</a></p>&mdash; James Sprinks (@spacepasty) <a href="https://twitter.com/spacepasty/status/669470892280422401">November 25, 2015</a></blockquote>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>

A good example of reuse of the "Where On Mars?" building blocks was during the [Mendeley "Mars Hack"](https://github.com/nmanaud/mendeley-mars-hack), where we explored the idea of *geo-referencing and visualising scientific publications on a map*, in context with other data. You can see on the interactive visualisation below the distribution of some of the scientific papers relating to Mars in the [Mendeley catalog](https://www.mendeley.com/research-papers/), as well as the journey of Mark Watney in the movie "The Martian", and the ExoMars's Rover and EDM landing sites (use full-screen mode for better experience):


<iframe width="100%" height="520" frameborder="0" src="https://whereonmars.carto.com/viz/eacbae98-8f8b-11e5-afdf-0e3ff518bd15/embed_map" allowfullscreen webkitallowfullscreen mozallowfullscreen oallowfullscreen msallowfullscreen></iframe>

*Context starts to bring insights and fun!*

<br/>

## WHAT'S NEXT?

Conducting this project and collaborating with developers, scientists, and the open data community has been a fun and rewarding experience. But we believe we can and should offer more!

### Space exploration and data deluge

*The data deluge is also coming from our solar system!* And we can expect an increasing interest of the general public for planetary science and the human exploration of other worlds, starting with the Moon and Mars!

> Why only telling stories about the ExoMars 2020 mission? Why not making it possible to tell stories about everything that happen or exist on Mars? Clouds, dust storms, dunes, landings, discoveries, celestial events, resources, human settlement, etc.. ?

Planetary satellite images and maps are being increasingly produced by the scientific community, and typically shared as images, in scientific publications, presentations, and news media websites. However, static images lack interactivity and contextual information, and are therefore not immediately accessible for further exploration and understanding.

We believe that interactive web maps are a powerful way of *telling stories*, *communicating* and *educating* people who, over the last decade, have become familiar with tools such as Google Maps. A few excellent planetary web map interfaces exist but they are either too complex to use for non-experts (E.g.: [PDS Geosciences Node Orbital Data Explorer (ODE)](http://ode.rsl.wustl.edu/)), or are closed-systems (E.g.: [Mars Trek](http://marstrek.jpl.nasa.gov/)) that do not allow anyone to publish and share their content on.

 **We are missing an Open Planetary Mapping platform to easily create and share geospatial data sets, basemaps and map visualisations**.

<!-- There is potential to help close the bride between scientists and the general public. -->

Recently, we announced that "Where On Mars?" had a new home within the *OpenPlanetary* community and framework.

*So, what's the plan?*

<div style="margin-bottom: 2em;">
<blockquote class="twitter-tweet" data-lang="en"><p lang="en" dir="ltr">&quot;Where On Mars?&quot; project has a new home <a href="https://twitter.com/openplanetary">@openplanetary</a> ! :) <a href="https://t.co/ube207AMC4">https://t.co/ube207AMC4</a> <a href="https://twitter.com/hashtag/opendata?src=hash">#opendata</a> <a href="https://twitter.com/hashtag/dataviz?src=hash">#dataviz</a> <a href="https://twitter.com/hashtag/maps?src=hash">#maps</a> <a href="https://twitter.com/hashtag/Mars?src=hash">#Mars</a> <a href="https://t.co/YUKwlPgvxP">pic.twitter.com/YUKwlPgvxP</a></p>&mdash; Where On Mars? (@whereonmars) <a href="https://twitter.com/whereonmars/status/776038854075805700">September 14, 2016</a></blockquote>
</div>
<script async src="//platform.twitter.com/widgets.js" charset="utf-8"></script>


### #OpenPlanetaryMap

Well, the plan is essentially to propose and help building an Open Planetary Mapping platform using "Where On Mars?" building blocks with the support of experts from within the OpenPlanetary community, as well as with any potential users of such a platform; including content creators, communicators, and consumers.

Here are a few ideas, paths we could take and experiment with, for starting an *OpenPlanetaryMap* initiative together:

- Crowdsourcing an open repository of Mars geospatial data sets, basemaps, map visualisations
- Building a web interface exposing content from this open repository
- Researching how to create an emotional connection with Mars for everyone
- Designing the most beautifully crafted and engaging interactive map of Mars
- Seeking kick-starter funding (ok, may be that one should be first! ;)
- Moving on to the next planet!

<br/>

## WE NEED YOUR FEEDBACK!

Whether you are a *planetary scientist*, *teacher*, *science journalist*, *student* or *space enthusiast* we need your feedback. **Please drop us a comment below**, short or long, to tell us what you think of this *#OpenPlanetaryMap* initiative, and if and how you would like to contribute.

Thank you!

<br/>
