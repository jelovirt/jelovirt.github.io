---
layout: post
title: Updated DITA-OT PDF plug-in generator, added `&lt;dl>` styling. I've never liked the DITA-OT default of styling...
---
Updated DITA-OT PDF plug-in generator, added `&lt;dl>` styling. I've never liked the DITA-OT default of styling `&lt;dl>` as a table, but that makes sense since `&lt;dl>` has a header and e.g. HTML style definition list doesn't really have a good place for a header. Anyhow, I added three `&lt;dl>` outputs: table, HTML style, and a bullet list. In the bullet list the definition term comes out in it's own row, but at some point I'll add another bullet list output where the term is in the same block as the definition, perhaps separated with a m-dash.

What I really should do is add example graphics, something that shows what the output is like for a given option. Maybe scans of pencil drawings?

#dita-ot