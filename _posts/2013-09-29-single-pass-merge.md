---
published: false
---

---
title: Single pass merge
---
Back in DITA-OT 1.6, I fixed [#1060](https://github.com/dita-ot/dita-ot/issues/1060) to reduce the amount of memory DITA-OT was using when merging map and topics into a single file. It was wasting memory by doing silly things, like writing XML to a string buffer, converting the buffer to a string, and back to string buffer again. My fix then was to use a single byte array and in the process convert the part of the code to use SAX pipes. Memory consumption went down, but it still needs parse intermediate process results and that is both slow and ugly.

I started to refactor the code, by changing the map and topic readers to write to a single SAX content handler. This would make the whole process a single pipe, allowing for more modular code and perhaps better performance. Once I had changed the unit tests to match the new code, I realized that the output would be different in a single pass process. The old code serialized maps and topics into separate buffers, and the merged file had them as siblings. When you only have one buffer and the merging process is map driven, topic references from the map and the actual topic will be interlaced:

     <map>
       <topic id="topic">
         ...
       </topic>
       <topicref href="topic.dita"/>
     </map>

The actual order can be changed, but still the same applies: the output order will not be the same. You could always post-process the output with XSLT to make the merged file match the old output, but that's extra processing you don't really want.

Not sure how I'll go about this. One way to solve this would be to read the map into a DOM document, collect all topic references, and then output the map first or last into the output content handler. Regardless the approach, I just have to follow the old workflow: refactor the code, measure the difference, and make a decision whether to keep the new code or not.

\#dita-ot