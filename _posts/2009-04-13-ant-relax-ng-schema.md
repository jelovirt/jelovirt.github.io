---
title: "Ant RELAX NG schema"
layout: post
tags: ant programming relax-ng
---
I use [oXygen](http://www.oxygenxml.com/) to edit [Ant](http://ant.apache.org/) build files and it uses a DTD for the schema. While that works well, the DTD has a few bugs and AFAICT does not support Ant 1.7. So, I wrote a [RELAX NG](http://relaxng.org/) schema for Ant.

The choice between schema languages was easy, RELAX NG has everything I need and is pleasant to write. In addition, oXygen can use the documentation in the schema, so all the better. I used [Trang](http://code.google.com/p/jing-trang/) to convert the original DTD to RELAX NG, then just edited the filed manually and occasionally with XSLT.

The code is hosted at [GitHub](http://github.com/jelovirt/ant-relaxng), licensed under GPL. It's very much a work in progress, but it works for me.

