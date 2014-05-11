---
title: "MIME Media Type for DITA"
layout: post
tags: dita mime-type
---
I've been wondering for a while now that why wasn't registration of MIME Media Type for DITA included into the 1.1 spec? Methinks it would look something like this.

<blockquote>
<dl>
<dt><strong>MIME media type name</strong>:</dt>
  <dd>application</dd>
<dt><strong>MIME subtype name</strong>:</dt>
    <dd>dita+xml</dd>
<dt><strong>Required parameters</strong>:</dt>
    <dd>None.</dd>
<dt><strong>Optional parameters</strong>:</dt>
    <dd>
    <dl>
        <dt>charset:</dt>
        <dd>This parameter has identical semantics to the charset parameter of the application/xml media type as specified in \[RFC3023\].</dd>
     </dl>
     </dd>
<dt><strong>Encoding considerations</strong>:</dt>
    <dd>By virtue of DITA content being XML, it has the same considerations when sent as "application/dita+xml" as does XML. See [RFC 3023, section 3.2](http://rfc.net/rfc3023.html#s3.2).</dd>
<dt><strong>Security considerations</strong>:</dt>
    <dd>[<i>Something about conref.</i>]</dd>
<dt><strong>Interoperability considerations</strong>:</dt>
   <dd>[<i>Haven't thought about this yet.</i>]</dd>
<dt><strong>Additional information</strong>:</dt>
<dd>
<dl>
    <dt>Magic number(s):</dt>
    <dd>There is no single initial octet sequence that is always present in DITA documents.</dd>
    <dt>File extension(s):</dt>
    <dd>DITA documents are most often identified with the extensions ".dita" or ".ditamap".</dd>
    <dt>Macintosh File Type Code(s):</dt>
    <dd>TEXT</dd>
</dl>
</dd>
<dt><strong>Intended usage</strong>:</dt>
    <dd>COMMON</dd>
<dt><strong>Author/Change controller</strong>:</dt>
    <dd>The DITA  specification is a work product of the OASIS' DITA TC. The OASIS has change control over these specifications.</dd>
</dl>
</blockquote>
This would allow us to change the definition of the <code>format</code> attribute e.g. in links into being a MIME Media Type, not a file extension.

<h2>Update</h2>

Three years later a MIME Type was added in [DITA 1.2](http://docs.oasis-open.org/dita/v1.2/os/spec/non-normative/DITA-mime-type.html).

