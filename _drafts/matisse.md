---
layout:     post
title:      "MATISSE"
subtitle:   "The ASDC web-tool to access, analyze and visualize planetary data"
author:     azinzi
header-img:
category: Community
tags: [database, Rosetta, Dawn, shape model, 3D, cartography, tutorial, VESPA, ODE REST, GIS]
slack_channel: 
image:
---

##MATISSE

[MATISSE](http://tools.asdc.asi.it/matisse.jsp) (Multi-purpose Advanced Tool for the Instruments for the Solar System Exploration) is a tool developed by [ASDC](http://www.asdc.asi.it/) since early 2013, with the purpose of improving both the accessibility of planetological data and their visualition directly on the 3D shape model of the selected object.

Using both public and proprietary data, thanks to several collaborations, currently MATISSE allows access to dataset from 6 different targets (the Moon, Mercury, asteroids 4 Vesta and 21 Lutetia, comet 67P Churyumov-Gerasimenko and dwarf planet 1 Ceres) and, by means of a MySQL database, it is possible to perform queries based on temporal, geographical (latitude, longitude) and geometrical (incidence, emission and phase angles) metadata [Fig 1].
Its modular structure also allows the tool to be extended to other datasets, and the possibility to connect to external repositories, using standards such as those of [Planetary Virtual Observatory](http://voparis-europlanet.obspm.fr/utilities/Erard_VOParis_PV2011_proceedings.pdf) and [NASA ODE REST API](http://nesf2014.arc.nasa.gov/sites/default/files/poster-pdfs/Bennett_Keith.pdf), is in its initial phase.

At the present time NASA ODE REST API has been used to provide access to NASA Messenger MDIS-NAC observations of Mercury, which can be searched and accessed directly from MATISSE. In the next future a strong collaboration with the VESPA team (already started) will likely introduce new features, such as the possibility of querying open access datasets from ESA PSA or using features implemented in PlanetServer for Mars and Moon hyperspectral data.

In the next future the collaborations with scientific teams of Rosetta and Dawn will introduce new features, such as:
+	Calculation of the aerodynamic coefficients for spherical and aspherical dust grains (useful for comparison with GIADA data)
+	Dust distribution map views of the released GIADA data
+	Retrieval of VIS/IR absorption bands and spectral indices
+	Retrieval of content of specific minerals

MATISSE generates higher-order outputs, such as false colors (RGB), ratios, mosaics and differences, computed on demand starting from the single observations available in the archive.

All its outputs can be viewed directly on the web (in 3D and 2D) or downloaded for offline use with external software (i.e., 2D FITS, GeoTIFF and ENVI; 3D [Paraview](http://www.paraview.org/)).

To access the tool, go to [its homepage](http://tools.asdc.asi.it/matisse.jsp) and follow the instructions described in the [User Manual](http://tools.asdc.asi.it/download/MATISSEv1-2.pdf).

Here you can find the published paper on [Astronomy and Computing](http://www.sciencedirect.com/science/article/pii/S2213133716300154) (here the [ArXiv](http://arxiv.org/abs/1603.05413) link).

##Tutorial

Here a brief example of MATISSE usage follows. When the homepage of the tool is loaded select “4 Vesta” as target and “VIR IR” as instrument. Then fill the latitude and longitude fields of the search form with the values Lat Min = 25, Lat Max = 40, Lon Min = 48, Lon Max = 63 and the click the “Search” button (you can of course change all these settings).

From the list of observations select the third one and then choose 5005.37 nm as wavelength and “Red temperature” as palette (the 5 micron band is best suited for thermal analysis).
After clicking the “Submit” button and waiting a pair of minutes the output page will be loaded: on the left the 3D interactive window is available, with the two 2D projected images (zoomed to the selection and covering the entire target) on the right. The links below them allows the download of the PostScript version of this images, whereas at the bottom of the page the links to download 2D GIS and 3D Paraview files will be located.

These are TGZ compressed files containing, respectively, 4 and 2 files: the 2D files are a GeoTIFF one and an ENVI IMG+HDR couple (with a readme.txt attached). In the 3D TGZ, along with the readme.txt a VTP file is present: this file can be opened with Paraview.
