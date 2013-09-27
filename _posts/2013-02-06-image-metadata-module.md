---
layout: post
title: Image metadata module
---
Commited ImageMetadataModule code to DITA-OT. It's a preprocessing module that adds image metadata to image elements, so the temporary files will have something like

    <image class="- topic/image " href="img.png" placement="inline"
           dita-ot:image-height="95" dita-ot:image-width="135"
           dita-ot:horizontal-dpi="100"  dita-ot:vertical-dpi="100"/>

This replaces the XSLT Java extension ImgUtils. The new code is thread-safe, caches image metadata, reads all metadata in one go where the old extension read each file twice, and once other Java extension are removed, Saxon version can be updated. I enabled it in XHTML based transtypes, but will need to implement the change to ODT and RTF transtypes too.

\#dita-ot