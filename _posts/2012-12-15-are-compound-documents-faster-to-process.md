---
layout: post
title: Are compound documents faster to process?
---
There are various DITA-OT optimization ideas I've been collecting over time and I think next I'll try one where filter and debug step will result in a single composite document that has all the DITA topics and maps. This is basically what the current merging code does, except all maps would be included, not just the start map. This way, all the following preprocessing steps could be done on just one document.

This optimisation makes the assumption that parsing a single large document is faster than parsing multiple small ones. I think I should test this before starting to write any code by generating two sets of documents

* 1000 topic files and 10 map files
* 1 compound file with 1000 topics and 9 maps, and 1 map file

This would give me some idea about the difference in processing time. It would be nice to work with a single compound file with 1000 topic and 10 maps, but OT has not way of specifying which of those maps in the compound file in the start map.

(fast-forward 30 minutes)

Ok, that's interesting. I created a test set with 300 topics and a single map. Each topic had

* 10 paragraphs
* 5 key references
* 2 content references
* 5 related links

The compound version is about 10% faster. I was expecting more.

\#dita, #dita-ot