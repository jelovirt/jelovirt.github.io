---
title: "Optimizing DITA-OT XSLT stylesheets"
layout: post
tags: dita-ot
---
The way DITA-OT currently uses XSLT patterns and expressions to match per element type is highly inefficient.

    *[contains(@class, ' task/task ')]/*[contains(@class, ' topic/title ')]
    
By using a wildcard in the element test, the XSLT processor is forced to check every element predicate.

What if DITA-OT contained an optimization, that rewrote element names on initial normalization stage and then
used that information later on in the processing to optimize for example XSLT processing. Since in DITA the actual
element name doesn't matter, all elements could be rename to "x". A task topic

    <task class="- topic/topic task/task " id="test">
      <title class="- topic/title ">Test</x>
    </task>

could be rewritten as

    <x class="- topic/topic task/task " id="test">
      <x class="- topic/title ">Test</x>
    </x>

without loosing any relevant information. This naturally assumes all processing in DITA-OT uses the `class` attribute.

If we can do this, then why not normalize every element name to the base topic element name. That is, normalize to

    <topic class="- topic/topic task/task ">
      <title class="- topic/title ">Test</x>
    </topic>
    
This could then be used to rewrite XPath and XSLT patterns to

    topic[contains(@class, ' topic/topic ')]/title[contains(@class, ' topic/title ')]

The XSLT processor would be able to optimize the expression evaluation and only need to check the predicate for elements that
might apply.

Changing the element name normalization is trivial, but XSLT stylesheet compilation would not be as easy. This is because if we have
an expression such as

    *[contains(@class, ' hi-d/b ')]

The expression itself doesn't tell us that the base element type is `ph`. This information would need to be extracted from the
schemas, and since two schemas could use the same specialization element name for two different base elements, we'd need to do this
for each schema. But, if the processor would assume unique element use, it would not be that bad.
