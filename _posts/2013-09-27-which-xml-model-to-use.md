---
layout: post
title: Which XML model to use
---
DITA-OT currently has places in the Java code where XML is passed from one object to another as String. Instead of parsing that at the receiving end, I would prefer to not serialize it in the first place and pass it as some object structure. The thing is, I can't decide which objects to use. One of the requirements is that the XML may be a node sequence, i.e. no single root element. So if I pass it as a DOM document, I would need to use a wrapper element for the root. I've also been thinking about a sequence of XMLEvents and Validator.nu's SAX Tree, as the receiving end in most cases will just add the content into a SAX stream. DITA-OT existing code uses DOM in most places, so I don't want to introduce e.g. XOM which would handle this nice with its Nodes sequence. Hmh, have to think about this a bit more still.

\#dita-ot