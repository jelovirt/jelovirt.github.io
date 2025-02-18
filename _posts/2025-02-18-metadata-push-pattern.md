---
title: Metadata push pattern
layout: post
tags: dita
---

Just like with related links, define metadata in a separate part of map.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
<map>
  <title>Map Title</title>
  <topicref href="topic.dita" keys="topic"/>

  <!-- push metadata -->
  <topicref keyref="topic" processing-role="resource-only">
    <topicmeta>
      <othermeta name="region" content="space"/>
    </topicmeta>
  </topicref>
</map>
```
