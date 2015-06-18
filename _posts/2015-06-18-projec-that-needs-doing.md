---
layout: post
title: Project that needs doing
tags: dita dita-ot
---
I've been working with DITA for more than 10 years and before that worked on proprietary vocabularies. In each case
the implementation picture is pretty much the same: authors use an editor, content is stored in a CMS, and deliverables
are published using a set of conversion. Editors and the content storage system have always required configuration and
integration, but most of the code written has gone into the conversion and the environment that handles the publishing
process. I call this the "publishing server" or "publishing service", and I've written one from scratch and done further
development on a few. I'd like to write yet another one, for DITA-OT.

The biggest reason for wanting to implement a conversion service for DITA-OT is that I think the world needs one. All
DITA enables content stores already have some method for publishing content, but that part is probably not their core
focus area and the features that make users happier are probably not in the details of the publishing system. On the other
end, small teams working without a CMS need to handle publishing locally, either from their editor or the command line, and
that seems to a pain point if you read the questions on DITA Users mailing list. Being able to use existing code that handles
all of that would save both money and time.

I'd really like to implement this, but I've already got far more spare-time OSS work that I can manage. I could take a year or so
off working on DITA-OT and just focus on this, but it's a "risk" I'd rather not take and I think my efforts are still needed for
DITA-OT itself. So now I'd need to find someone to finance this work. I'd be willing to work on this as a closed source project
and just work as a consultant, but I'd much rather have it be released as open source project to benefit the community and get
more parties involved.