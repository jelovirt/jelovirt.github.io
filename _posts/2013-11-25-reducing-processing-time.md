---
title: Reducing processing time
layout: post
---

A non-exhaustive list of configuration changes that can be used to reduce DITA-OT processing time:

## Disable debug attribute generation

The `lib/configuration.properties` file has a property `generate-debug-attributes`. By changing the value to `false`, DITA-OT will no longer generate the `xtrf` and `xtrc` debug attributes. This will make it more difficult to track down at which source file location a given issue may have originated from, but it will reduce the size of the temporary files. As a result, XML parsing will take less time and overall processing time will be reduced.

## Switch the order of conref and keyref processing

If your DITA source uses a lot of conrefs that in turn contain a lot of keyrefs, it may speed up processing if you reverse the order of the two in preprocessing. You simply need to have a copy the `preprocess` Ant target in your plug-in and change the order there. The DITA specification is a good example of this, as the processing time is reduced to less than half of the original time.

*Update:* Since DITA-OT 2.0, this is the default processing order.

## Use fast disk for temporary directory

DITA-OT keeps topic and map files as separate files and processes each file multiple times during preprocessing. Thus reading from disk, parsing XML, serializing XML, and writing to disk makes processing quite IO intensive. Use either an [SSD](http://en.wikipedia.org/wiki/Solid-state_drive) or a [RAM disk](http://en.wikipedia.org/wiki/RAM_drive) for temporary files, and never use a temporary directory that is not located on the same machine as where the processing takes place.

## Reuse the JVM instance

For all but extremely large source sets the JVM will not have enough time to warm-up. By reusing the same JVM instance, the first few DITA-OT conversions will be "normal", but when the JIT starts to kick in, the performance increase may be 2-10 fold. This is especially noticeable with smaller source sets, as much of the DITA-OT processing is I/O intensive.
