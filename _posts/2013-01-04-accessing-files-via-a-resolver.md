---
layout: post
title: Accessing files via a resolver
---
One of the features I've been planning for DITA-OT.next is a the adoption of a URIResolver/EntityResolver that is used for accessing all temporary files. That is, all Java code would retrieve the files with the resolver instead of opening input streams to files and all files would be written with those resolvers.

The benefit is that once you access all resources via the resolvers, the resolvers can:

* Write and read files to memory only. DITA-OT processing is I/O intensive and disks are slow.
* Keep files in parsed format or in a format that is faster to parse than XML. This could be e.g. DOM or Saxon's PTree.

To support extensibility, there would need to be an Ant task to serialize the temporary content into plain XML in a temporary file. Then, the default processing kicks in again, it would read the XML files from the temporary directory and e.g. keep them in memory as PTrees.

\#dita-ot #dita-ot-next