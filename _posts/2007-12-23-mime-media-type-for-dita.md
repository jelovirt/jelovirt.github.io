---
title: "MIME Media Type for DITA"
layout: post
tags: dita mime-type
---
I've been wondering for a while now that why wasn't registration of MIME Media Type for DITA included into the 1.1 spec? Methinks it would look something like this.

<strong>MIME media type name</strong>:

application

<strong>MIME subtype name</strong>:

dita+xml

<strong>Required parameters</strong>:

None.

<strong>Optional parameters</strong>:

charset:

This parameter has identical semantics to the charset parameter of the application/xml media type as specified in \[RFC3023\].

<strong>Encoding considerations</strong>:

By virtue of DITA content being XML, it has the same considerations when sent as "application/dita+xml" as does XML. See [RFC 3023, section 3.2](http://rfc.net/rfc3023.html#s3.2).

<strong>Security considerations</strong>:

\[<i>Something about conref.</i>\]

<strong>Interoperability considerations</strong>:

\[<i>Haven't thought about this yet.</i>\]

<strong>Additional information</strong>:

Magic number(s):

There is no single initial octet sequence that is always present in DITA documents.

File extension(s):

DITA documents are most often identified with the extensions ".dita" or ".ditamap".

Macintosh File Type Code(s):

TEXT

<strong>Intended usage</strong>:

COMMON

<strong>Author/Change controller</strong>:

The DITA  specification is a work product of the OASIS' DITA TC. The OASIS has change control over these specifications.

This would allow us to change the definition of the <code>format</code> attribute e.g. in links into being a MIME Media Type, not a file extension.

<h2>Update</h2>

Three years later a MIME Type was added in [DITA 1.2](http://docs.oasis-open.org/dita/v1.2/os/spec/non-normative/DITA-mime-type.html).

