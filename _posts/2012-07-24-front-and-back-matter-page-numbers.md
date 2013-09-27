---
layout: post
title: Front and Back Matter page numbers
---
Would like to add a feature to DITA-OT PDF plug-in generator which would allow using roman numbering in front and back matter, and have back matter continue from front matter page numbering. E.g. if the last page of front matter is xii, the first page of back matter would be xiii. This is what Chicago Manual of Style, 15th edition, 1.106 recommends.

The problem is, XSL FO doesn't enable this. If your could use:

    <fo:page-sequence initial-page-number="x:page-number-citation-last(front-matter-sequence-id) + 1">

that would probably work. Alas, AntennaHouse XSL Formatter doesn't have an extension for this, nor does XSL 2.0 that something like this planned.

\#dita-ot #xsl-fo