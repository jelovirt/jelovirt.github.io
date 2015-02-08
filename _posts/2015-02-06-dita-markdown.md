---
title: "Markdown DITA"
layout: post
tags: dita-ot markdown
---
DITA 1.2 spec defines a *DITA document* as:

> An XML document that conforms to the requirements of this specification.

Like [@Ditaguy](https://twitter.com/Ditaguy) with Lightweight DITA, I think a DITA document doesn't have to be XML. While is doesn't conform to the DITA spec, I wrote [DITA-OT Markdown plug-in](https://github.com/jelovirt/dita-ot-markdown) that allows using Markdown documents with DITA topic and maps. Markdown is converted to DITA topics during preprocessing and all transtype specific code will only see DITA XML documents.

Once I polish the code, I'll define the constraints DITA imposes on the Markdown document. Right now, the implementation requires that Markdown topics start level 1 header and contain only one level 1 header; all other header levels are treated as section titles.

## Example

test.ditamap:

    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE map PUBLIC "-//OASIS//DTD DITA Map//EN" "map.dtd">
    <map>
      <topicref href="test.md" format="markdown"
                keys="key"/>
      <keydef keys="image-key" href="test.png"/>
    </map>

test.md:

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
    
    Images
    ------

    An inline ![Alt](test.png).

    ![Alt](test.png)

    ![Alt](test.png "Title")

    ![image-key]

    Links
    -----
    
    *   [Markdown](test.md)
    *   [DITA](test.dita)
    *   [HTML](test.html)
    *   [External](http://www.example.com/test.html)
    *   [key]

The test.md Markdown topic is equivalent to XML topic:

    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE topic PUBLIC "-//OASIS//DTD DITA Topic//EN" "topic.dtd">
    <topic id="x">
      <title>Test</title>
      <body>
        <p>Paragraph <i>test</i> and <b>list</b>:</p>
        <ul>
          <li>hyphen</li>
          <li>list</li>
          <li>item</li>
        </ul>
        <ul>
          <li>asterix
            <ul>
              <li>list</li>
            </ul>
          </li>
          <li>item
            <ul>
              <li>nested</li>
            </ul>
          </li>
        </ul>
        <ol>
          <li>ordered</li>
          <li>list</li>
          <li>item
            <ol>
              <li>nested</li>
              <li>list</li>
            </ol>
          </li>
        </ol>
        <p>Code example on <codeph>for</codeph> loop:</p>
        <codeblock>for i in items:
        println(i)
    </codeblock>
        <section>
          <title>Images</title>
          <p>An inline <image href="test.png"><alt>Alt</alt></image>.</p>
          <image href="test.png">
            <alt>Alt</alt>
          </image>
          <fig>
            <title>Title</title>
            <image href="test.png">
              <alt>Alt</alt>
            </image>
          </fig>
          <image keyref="image-key"/>
        </section>
        <section>
          <title>Links</title>
          <ul>
            <li>
              <xref href="test.md">Markdown</xref>
            </li>
            <li>
              <xref href="test.dita">DITA</xref>
            </li>
            <li>
              <xref href="test.html" format="html">HTML</xref>
            </li>
            <li>
              <xref href="http://www.example.com/test.html" format="html" scope="external">External</xref>
            </li>
            <li>
              <xref keyref="key"/>
            </li>
          </ul>
        </section>
      </body>
    </topic>

Processing requires that `format="markdown"` is used to declare a Markdown file as DITA; exception to this are links in Markdown topics, where file extensions `.md` and `.markdown` will make DITA-OT treat target files are Markdown DITA. I don't particularly like format detection based on file extensions, but this is needed due to limitations in Markdown syntax.
