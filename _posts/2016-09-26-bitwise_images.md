---
layout:     post
title:      "How the PDS data format works"
subtitle:   
author:     cmillion
header-img:
category: Tools
tags: [PDS, images, Python]
slack_channel: tools
image:
---

Despite the labels / metadata often being somewhat complicated to parse, as discussed in [a previous post by Trent Hare](https://openplanetary.github.io/blog/tools/pds-interoperable-format.html), the PDS image format is actually pretty simple at its core. This is by design: as an "archival" image format, it needs to be more or less self-describing so that some future programmer in ten or fifty years can figure out how to read the file by inspection alone--that is, just by looking at the file contents--with perhaps a small assist from some plaintext documentation. (This is a "fun" exercise; if you're into such things, you should stop reading now and go do it.) This means that if you don't have a PDS data reader available in your language of choice--because you are super hip and use [new](https://en.wikipedia.org/wiki/Julia_(programming_language)) or [unusual](https://en.wikipedia.org/wiki/Whitespace_(programming_language)) languages--then you should be able to hack one together pretty quickly.

Such files are generally formatted thusly:
* There is a header that contains metadata in some plaintext (ASCII) markup format. Because it's in plaintext, you can read it by just opening the file in a text editor (or, e.g., by using the command line `less` or `more` tools).
* Some parameter in the header defines the extent of the header either in terms of a number of bytes or a terminal string.
* Some parameter(s) in the header define the image height and width in pixels. If it is a multi-frame image, then there may also be a term defining the number of frames.
* Some parameter in the header defines the number of bytes assigned to each pixel of the image (the "bit-depth"). Some other parameter defining the [endianness](https://en.wikipedia.org/wiki/Endianness) of the pixel data.

So to read the image, you must only do the following:
* Search through the header for the aforementioned parameters and store their values.
* Skip to the end of the header. You should now be at the beginning of the image.
* Read the file out in chunks equal to the bit-depth. Convert the binary into a floating point using the appropriate endian. Store each floating point equivalent in an element of an array with the same number of of elements as the image has pixels (e.g. height x width x frames).
* Stop when you're out of pixels.
* Reshape the array if necessary.

As an example, [here is code that I wrote to work with MER Pancam images](https://github.com/cmillion/pds-util/blob/master/src/pds.py). (Note that if I were redoing this now, I would use [w10n](http://openplanetary.co/blog/tools/w10n.html#comment-2908161700) or [planetaryimage](https://github.com/planetarypy/planetaryimage).)

That formula will get you most of the way there most of the time. There may be slight variations, for which you might want to consult appropriate documentation. For example, you might need to apply some kind of bit mask to the binary data.

Conveniently, the PDS image format is also very similar to a number of other archival digital data formats, including [FITS](https://en.wikipedia.org/wiki/FITS) and [SER](https://free-astro.org/index.php/SER), so much of the above may be reusable in those cases. It seems that several groups independently arrived at the same solution in designing these formats or cribbed from the same solution. (It's a good solution!)

Handling the metadata in a robust way is still hard, though.
