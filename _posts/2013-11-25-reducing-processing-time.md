---
title: Reducing processing time
layout: post
---

A non-exhaustive list of configuration changes that can be used to reduce DITA-OT processing time:

## Disable debug attribute generation

The `lib/configuration.properties` file has a property `generate-debug-attributes`. By changing the value to `false`, DITA-OT will no longer generate the `xtrf` and `xtrc` debug attributes. This will make it more difficult to track down at which source file location a given issue may have originated from, but it will reduce the size of the temporary files. As a result, XML parsing will take less time and overall processing time will be reduced.

## Switch the order of conref and keyref processing

If your DITA source uses a lot of conrefs that in turn contain a lot of keyrefs, it may speed up processing if you reverse the order of the two in preprocessing. You simply need to have a copy the `preprocess` Ant target in your plug-in and change the order there. The DITA specification is a good example of this, as the processing time is reduced to less than half of the original time.
