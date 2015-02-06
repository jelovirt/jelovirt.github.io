---
title: "Markdown DITA"
layout: post
tags: dita-ot markdown
---
DITA 1.2 spec defines a *DITA document* as:

> An XML document that conforms to the requirements of this specification.

Like [@Ditaguy](https://twitter.com/Ditaguy) with Lightweight DITA, I think a DITA document doesn't have to be XML. While is doesn't conform to the DITA spec, I wrote [DITA-OT Markdown plug-in](https://github.com/jelovirt/dita-ot-markdown) that allows using Markdown documents with DITA topic and maps. Markdown is converted to DITA topics during preprocessing and all transtype specific code will only see DITA XML documents.

Once I polish the code, I'll define the constraints DITA imposes on the Markdown document. Right now, the implementation requires that Markdown topics start level 1 header and contain only one level 1 header; all other header levels are treated as section titles. For example, the following Markdown DITA and XML DITA are equivalent:

```markdown
# Test

Paragraph *test* and **list**:

-   hyphen
-   list
-   item

*   asterix
    *   list
*   item
    *   nested

1.  ordered
1.  list
1.  item
    1.  nested
    1.  list

Code example on `for` loop:

    for i in items:
        println(i)

Links
-----

*   [Markdown](test.md)
*   [DITA](test.dita)
*   [HTML](test.html)
*   [External](http://www.example.com/test.html)
```

```xml
<topic id="x">
  <title>Test</title>
  <body>
    <p>Paragraph <i>test</i> and <b>list</b>:</p>
    <ul>
      <li>hyphen</li>
      <li>list</li>
      <li>item</li>
      <li>
        <p>asterix</p>
        <ul>
          <li>list</li>
        </ul>
      </li>
      <li>item<ul><li>nested</li></ul></li>
    </ul>
    <ol>
      <li>ordered</li>
      <li>list</li>
      <li>item<ol><li>nested</li><li>list</li></ol></li>
    </ol>
    <p>Code example on <codeph>for</codeph> loop:</p>
    <codeblock>for i in items:
    println(i)
</codeblock>
    <section>
      <title>Links</title>
      <ul>
        <li>
          <xref href="test.md" title="" type="topic">Markdown</xref>
        </li>
        <li>
          <xref href="test.dita" title="">DITA</xref>
        </li>
        <li>
          <xref href="test.html" format="html" title="">HTML</xref>
        </li>
        <li>
          <xref href="http://www.example.com/test.html" format="html" scope="external" title="">External</xref>
        </li>
      </ul>
    </section>
  </body>
</topic>
```
