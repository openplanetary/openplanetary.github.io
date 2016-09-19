---
layout:     post
title:      "Does the NASA PDS image format make for a good interoperable format?"
subtitle:   "reposted from planetarygis.blogspot.com"
author:     thare
category: Tools
tags: [PDS, format]
image:
---

It could be but that is not its purpose in life.  This post was
inspired by question, "why not make PDS exporting (or conversion from
Geotiff) available from the [NASA AMES Stereo Pipeline](https://ti.arc.nasa.gov/tech/asr/intelligent-robotics/ngt/stereo/)." 
This was my answer. Please note this is IMHO - please feel free to disagree.

## Background

So I assume there are many PDS3 (and now some PDS4) writers out there.
I actually don't know of a robust GeoTiff to PDS image converter. In
general, I view the PDS (3 or 4) format as really an "archival" format
and not necessarily a good format to support interoperability between
applications. Okay so what's the difference? Archive formats are meant
to be "simple" to use and should have verbose labels to access the
data for years into the future. Sounds great - what's the problem? In
particular, PDS archives can have metadata spread across multiple
files which describe the mission, image label particulars, the map
projection equations (which may not be  typical equations, if even map
projected at all), etc., which makes a single image file less self-
contained. Thus not only should a PDS *.IMG (image with label) be
created, but to be a valid PDS archive, there should also be other
informational files created in a structured set of directories. When
GeoTiffs are used for archives (more common for Earth data sets), they
actually have the same metadata problem, which is usually solved by
using an FGDC/ISO metadata file sitting directly next to the GeoTiff
(extension *.tif.xml).

Okay - I don't care about metadata, I just want to write out a PDS
*.IMG format. Above, I stated there are probably dozen of PDS writers
out there. The main reason there are so many is because the folks
writing these files must target their labels for their particular
mission. It would be a challenge to create a generic PDS label
creation/conversion solution. Many portions of the required metadata
cannot be 100% automated (whether PDS or FGDC metadata). For example
for PDS, there are many keywords that the user should supply that
would need to be (manually) defined during conversion (e.g.
PRODUCED_ID, PRODUCER_FULL_NAME, INSTRUMENT_HOST_NAME, etc.). Check
out any *.lbl from [here](http://pds-geosciences.wustl.edu/lro/lro-l-lola-3-rdr-v1/lrolol_1xxx/data/lola_gdr/cylindrical/float_img/) .

All that said, both ISIS3 and VICAR can convert to a "generic" PDS v3
label, but it will not be a fully archive-able PDS label. To help with
the mission particulars, you will notice ISIS3 has a unique PDS export
routine for each instrument (when that instrument is supported for PDS
export, e.g. lrocnac2pds, lrowac2pds, mrf2pds - [https://isis.astrogeology.usgs.gov/Application/index.html#Lunar_Orbiter](https://isis.astrogeology.usgs.gov/Application/index.html#Lunar_Orbiter) ).

Anyway, I am happy to share a very simple (hacky/brute force) gdal2PDS
(v3) Python writer but it would need to be highly tweaked depending on
the mission you are supporting. And I currently only support a couple
projections as used by the LMMP project. Did I say it was very hacky
-- use with caution: [http://github.com/USGS-
Astrogeology/GDAL_scripts/tree/master/gdal2ISIS3](http://github.com/USGS-Astrogeology/GDAL_scripts/tree/master/gdal2ISIS3)

Could a generic PDS3 writer be added to GDAL - yes. But PDS3 is slowly
getting supplanted by PDS4 so that would need to be added too. PDS4 is
XML based which can complicate simple writers. There are plans to add
in a PDS4 reader to GDAL once the format stabilizes. A reader should
be much more tangible than a generic writer (for map projected
products at least). Heck, we could even support a "raw" Geotiff with a
PDS 3 or 4 label pointing inside at the pixels, but raw Tiffs lose
many benefits like tiles and compression capabilities.

lots more information about PDS4: [http://sbndev.astro.umd.edu/wiki/PD
S4_Data_Structures](http://sbndev.astro.umd.edu/wiki/PDS4_Data_Structu
res)

_this post appeared originally on
[http://planetarygis.blogspot.com](http://planetarygis.blogspot.com)_
