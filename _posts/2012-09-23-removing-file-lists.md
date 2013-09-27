---
layout: post
title: Removing file lists
---
Spent a total of 7 hours yesterday on busses and used most of that time refactoring DITA-OT code. I moved the old key.list file into the Job class which contains the processing state and cleaned keydef.xml and schemekeydef.xml generation. I may be wrong, but I think I'm the only person in existence who cares about DITA-OT internals; or, it's not really that I care about it, it just annoys me to see code that was originally developed my multiple coders over time but it was never refactored to clean it.

As long a DITA-OT uses Ant XSLT task to drive the processing, we need to keep the list files around. But, I'm planning to replace dita.list with job.xml (or something like that), which initially contains the same information. Instead of storing comma separated lists, the job.xml will use an element for each file, thus we get rid of the restriction on commas in file names. I could use something more hip, like XAML or JSON, but I don't want to add new library dependencies to be able to parse and serialize the format, I will just use plain old XML. The next step after that will be to to merge cache and status files into job.xml, there's no added benefit in having keydef.xml or export.xml as separate files.

A longer term plan is to inverse how data about files is stored in job.xml, i.e. instead of having properties that have a file set as values, there will be a set of files and each will have properties associated with it. Something like:

    <file path="test.dita" format="dita" has-conref="true" is-target="true" first-id="GUID-123"/>

We can still keep the old list files for Ant tasks by just generating them from the cached data.

Exciting, isn't it?!?

\#dita-ot