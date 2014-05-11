---
title: "DITA Authoring DTD Generator"
layout: post
tags: authoring dita dita domain-specialization generator
---
A DITA authoring DTD generator for creating DTDs that are <em>not</em> valid specialization, but can be used for authoring purposes.<!--more--> See [DITA Architectural Specification](http://docs.oasis-open.org/dita/v1.1/OS/archspec/speclimits.html) for limits of specialization, in particular chapter "[Customized subset document types for authoring](http://docs.oasis-open.org/dita/v1.1/OS/archspec/speclimits.html#customsubset)" for description of specialization possibilities. For valid specializations, see [DITA Specialization Generator](/2007/12/09/dita-specialization-generator/).
<div class="note">
<strong>Note</strong>: There is a new version of the generator at [DITA DTD Generator](/dita-generator/). It does not enable all the possibilities offered here, but is more robust and support DITA 1.2.
</div>

<script type="application/javascript" src="/wp-content/uploads/2008/03/form.js"></script>
<form action="/cgi-bin/dtdgenerator.py" method="get" onsubmit="return validateForm(event);" style="text-align: left" target="_blank">
<table>
<tbody>
<tr>
  <th><label for="type">Base type</label>*</th>
  <td colspan="2"><select name="type" id="type" class="required"><option value=""></option><option value="topic">topic</option><option value="concept">concept</option><option value="task">task</option><option value="reference">reference</option></select></td>
  <td></td>
</tr>
<tr valign="top">
  <th rowspan="6">Domains</th>
  <td><input type="checkbox" name="domain" value="ui" /></td>
  <td>User interface</td>
  <td></td>
</tr>
<tr>
  <td><input type="checkbox" name="domain" value="hi" /></td>
  <td>Highlight</td>
  <td></td>
</tr>
<tr>
  <td><input type="checkbox" name="domain" value="pr" /></td>
  <td>Programming</td>
  <td></td>
</tr>
<tr>
  <td><input type="checkbox" name="domain" value="sw" /></td>
  <td>Software</td>
  <td></td>
</tr>
<tr>
  <td><input type="checkbox" name="domain" value="ut" />
  </td><td>Utilities</td>
  <td></td>
</tr>
<tr>
  <td><input type="checkbox" name="domain" value="indexing" /></td>
  <td>Indexing</td>
  <td></td>
</tr>
<tr valign="top">
  <th rowspan="2">Content-model rewrite</th>
  <td><input type="checkbox" name="remove" value="separate" /></td>
  <td>Block-inline separation</td>
  <td></td>
</tr>
<tr valign="top">
  <td><input type="checkbox" name="remove" value="foreigndata" />
  </td><td>foreign and data element removal</td>
  <td></td>
</tr>
<tr>
  <th><label for="root">Root element</label></th>
  <td colspan="2"><input type="text" name="root" id="root" class="xrequired" /></td>
  <td>Leave empty to override base topic root element.</td>
</tr>
<tr>
  <th><label for="nested">Nested topics</label></th>
  <td colspan="2"><input type="checkbox" name="nested" id="nested" value="true" /></td>
  <td></td>
</tr>
<tr>
  <th>Global attributes</th>
  <td colspan="2"><textarea name="attribute">xtrc CDATA #IMPLIED&#xA;xtrf CDATA #IMPLIED</textarea></td>
  <td>Attributes that are added globally by integrating into <code>%global-atts;</code>. Contents of the field are used as is in the DTD files.</td>
</tr>
<tr>
  <th><label for="owner"><abbr title="Public Formal Identifier">PFI</abbr> owner</label></th>
  <td colspan="2"><input type="text" name="owner" id="owner" disabled="disabled" /></td>
  <td>For example a domain. PFI will not be used if empty.</td>
</tr>
<tr valign="top">
  <th rowspan="2">Download</th>
  <td colspan="2"><button type="submit" name="file" value="dtd">dtd</button> <button type="submit" name="file" value="mod">mod</button></td>
  <td></td>
</tr>
<tr valign="top">
  <td colspan="2"><button type="submit" name="file" value="tgz">all files</button></td>
  <td></td>
</tr>
</tbody>
</table>
* denotes required fields
</form>

