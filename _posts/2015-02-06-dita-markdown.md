---
title: "Markdown DITA"
layout: post
tags: dita-ot markdown
---
DITA 1.2 spec defines a *DITA document* as:

> An XML document that conforms to the requirements of this specification.

Like [@Ditaguy](https://twitter.com/Ditaguy) with Lightweight DITA, I think a DITA document doesn't have to be XML. While is doesn't conform to the DITA spec, I wrote [DITA-OT Markdown plug-in](https://github.com/jelovirt/dita-ot-markdown) that allows using Markdown documents with DITA topic and maps. Markdown is converted to DITA topics during preprocessing and all transtype specific code will only see DITA XML documents.

Once I polish the code, I'll define the constraints DITA imposes on the Markdown document. Right now, the implementation requires that Markdown topics start level 1 header and contain only one level 1 header; all other header levels are treated as section titles.

