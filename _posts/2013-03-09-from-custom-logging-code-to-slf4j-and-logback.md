---
layout: post
title: From custom logging code to SLF4J and Logback
---
Started the work to migrate from custom logging code to SLF4J and Logback. It's long overdue, but after I changed the Java code to directly log to Ant's loggers instead of standard err, the logging has been working well enough. As I move the code to use SLF4J, I'll probably also change the way log messages are configured, the current way doesn't offer us anything that more common approaches will. This is really boring work, but I think it needs to be done. #dita-ot