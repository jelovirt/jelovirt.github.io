---
layout: post
title: Topic Merge as SAX
---
Rewrote topic merging in DITA Open Toolkit to use SAX filters and a single ByteArrayOutputStream and the memory consumption went down from 681 MB to 275 MB (JVM max memory where the test still went through). Pretty good. I would have refactored the code to use a single SAX pipe, but the id attribute rewrite still requires some thinking. Anyhow, a step to the right direction: use more SAX filters.

\#dita-ot