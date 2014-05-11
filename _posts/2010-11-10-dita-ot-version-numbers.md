---
title: "DITA-OT version numbers"
layout: post
tags: dita dita-ot
---
I've never been a fan of the way DITA-OT versions its releases. When I see a version number <code>1.5.2</code>, I assume the numbering scheme is <em>major.minor.micro</em>, i.e. it's the second bug release to version <code>1.5</code>. DITA-OT, however, uses a scheme which is more or less <em>dita-major.ot-major.ot-minor</em> or you can think of the first number as a constant that doesn't mean anything. In addition to this, the development releases use the version number <code>1.5.2 M6</code>, using a space character as the separator.

The version scheme I'd prefer to see is what e.g. OSGi uses. That is, <em>major.minor.micro.qualifier</em>. Thus the current DITA-OT version number would be something like <code>5.2.0.M6</code>. I naturally wouldn't change version numbering at this release, but instead of making the next release <code>1.5.3</code> I would make that <code>2.0.0</code>. It would have made sense to do it at this stage to coincide with DITA 1.2 support, but it's too late now. Anyhow, then the releases could reserve the third version number for bug releases (which DITA-OT doesn't really ever release), and use the milestone version as the fourth part.



