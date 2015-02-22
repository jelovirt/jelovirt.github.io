---
title: "Markdown DITA"
layout: post
tags: dita-ot markdown
---
DITA 1.2 spec defines a *DITA document* as:

> An XML document that conforms to the requirements of this specification.

Like [@Ditaguy](https://twitter.com/Ditaguy) with Lightweight DITA, I think a DITA document doesn't have to be XML. While is doesn't conform to the DITA spec, I wrote [DITA-OT Markdown plug-in](https://github.com/jelovirt/dita-ot-markdown) that allows using Markdown documents with DITA topic and maps. Markdown is converted to DITA topics during preprocessing and all transtype specific code will only see DITA XML documents.

Since Markdown allows content models that are not compatible with DITA topics, Markdown DITA topics have the following restrictions:

* A topic must start with a level 1 header and contain only one level 1 header, or
* A topic must start with a [Pandoc title block](http://johnmacfarlane.net/pandoc/demo/example9/pandocs-markdown.html#extension-pandoc_title_block) and may then contain multiple level 1 headers
* Header levels 2-6 are treated as nested topics, except if they use header attribute extensions to add class `section` or `example`; in that case they are treated as `section` or `example` elements, respectively.

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
    
    ## Example {.example}
    
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
    <topic id="test">
      <title>Test</title>
      <body>
        <p>Paragraph <i>test</i> and <b>list</b>:</p>
        <ul>
          <li>hyphen</li>
          <li>list</li>
          <li>item</li>
        </ul>
        <ul>
          <li>asterix<ul><li>list</li></ul></li>
          <li>item<ul><li>nested</li></ul></li>
        </ul>
        <ol>
          <li>ordered</li>
          <li>list</li>
          <li>item<ol><li>nested</li><li>list</li></ol></li>
        </ol>
        <example id="example">
          <title>Example </title>
          <p>Code example on <codeph>for</codeph> loop:</p>
          <codeblock>for i in items:
        println(i)
    </codeblock>
        </example>
      </body>
      <topic id="images">
        <title>Images</title>
        <body>
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
        </body>
      </topic>
      <topic id="links">
        <title>Links</title>
        <body>
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
        </body>
      </topic>
    </topic>


Processing requires that `format="markdown"` is used to declare a Markdown file as DITA; exception to this are links in Markdown topics, where file extensions `.md` and `.markdown` will make DITA-OT treat target files as Markdown DITA. I don't particularly like format detection based on file extensions, but this is needed due to limitations in Markdown syntax.
