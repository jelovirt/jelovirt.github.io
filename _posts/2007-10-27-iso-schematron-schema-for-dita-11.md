---
title: "ISO Schematron schema for DITA 1.1 and 1.2"
layout: post
tags: dita dita schema schematron
---
*NOTE*: See [GitHub project pages](http://wiki.github.com/jelovirt/dita-schematron/) for current information. This page is retained as legacy placeholder.

ISO Schematron schema for DITA 1.1 and 1.2 that handles cases that DTDs or XML Schemas cannot control. The current implementation covers for example:

* nesting links inside links or titles</li>
* deprecated attributes and attributes</li>
* attributes not intended for author use.</li>

Download <a href="http://github.com/jelovirt/dita-schematron/downloads" title="Schematron for DITA distribution">latest version</a> from GitHub. The schema is released under [GNU Lesser General Public License](http://www.gnu.org/licenses/lgpl.html).

<h3>Usage</h3>

The schema comes in two parts,

* dita-1.1.sch
* dita-1.2.sch

for different DITA versions. The schema has three phases:

<dl>
<dt><code>specificationMandates</code></dt>
<dd>constraints in the DITA language specification prose</dd>
<dt><code>recommendations</code></dt>
<dd>constraints and recommendations in the DITA language specification prose</dd>
<dt><code>authoringRecommendations</code></dt>
<dd>recommendations for authors</dd>
</dl>
<h3>Change History</h3>

See [GitHub downloads](http://github.com/jelovirt/dita-schematron/downloads) for latest releases.

<table border="1">
<tr>
<th>Version</th>
<th>Date</th>
<th>Description</th>
<th>Download</th>
</tr>
<tr>
<td>1.0.0</td>
<td>2007-08-31</td>
<td>Initial release.</td>
<td><a href="/wp-content/uploads/2007/10/dita_100.sch" title="Schematron for DITA version 1.0.0">dita_100.sch</a></td>
</tr>
<tr>
<td>1.1.0</td>
<td>2007-09-17</td>
<td>Added deprecations.</td>
<td><a href="/wp-content/uploads/2007/10/dita_110.sch" title="Schematron for DITA version 1.1.0">dita_110.sch</a></td>
</tr>
<tr>
<td>1.1.1</td>
<td>2007-12-09</td>
<td>Added GNU LGPL.</td>
<td><a href="/wp-content/uploads/2007/12/dita_111.sch" title="Schematron for DITA version 1.1.1">dita_111.sch</a></td>
</tr>
<tr>
<td>1.2.0</td>
<td>2007-12-18</td>
<td>Added id attribute for elements with a title.</td>
<td><a href="/wp-content/uploads/2007/12/dita-120.sch" title="Schematron for DITA version 1.2.0">dita-120.sch</a></td>
</tr>
<tr>
<td>1.3.0</td>
<td>2007-04-01</td>
<td>Added indextermref. Corrected deprecated element message.</td>
<td><a href="/wp-content/uploads/2008/04/dita-130.sch" title="Schematron for DITA version 1.3.0">dita-130.sch</a></td>
</tr>
<tr>
<td>1.4.0</td>
<td>2008-04-02</td>
<td>Added rule for single paragraph.</td>
<td><a href="/wp-content/uploads/2008/04/dita-140.sch" title="Schematron for DITA version 1.4.0">dita-140.sch</a></td>
</tr>
<tr>
<td>1.5.0</td>
<td>2008-04-08</td>
<td>Added rule for spectitle in simpletable.</td>
<td><a href="/wp-content/uploads/2008/04/dita-150.sch" title="Schematron for DITA version 1.5.0">dita-150.sch</a></td>
</tr>
<tr>
<td>1.5.1</td>
<td>2008-04-08</td>
<td>Made spectitle rule more general and added specentry and no-topic-nesting rules.</td>
<td><a href="/wp-content/uploads/2008/04/dita-151.sch" title="Schematron for DITA version 1.5.1">dita-151.sch</a></td>
</tr>
<tr>
<td>1.6.0</td>
<td>2008-04-24</td>
<td>Added phased. Added patterns.</td>
<td><a href="/wp-content/uploads/2008/04/dita-160.sch" title="Schematron for DITA version 1.6.0">dita-160.sch</a></td>
</tr>
<tr>
<td>1.6.1</td>
<td>2008-06-09</td>
<td>Reorganized to remove Oxygen NVDL invalid error message.</td>
<td><a href="/wp-content/uploads/2008/06/dita-161.sch" title="Schematron for DITA version 1.6.1">dita-161.sch</a></td>
</tr>
<tr>
<td>1.7.0</td>
<td>2008-06-09</td>
<td>Changed phase name to clear that not all recommendations come from the spec.
Added source comments.
Added pre exclusions from HTML 4.</td>
<td><a href="/wp-content/uploads/2008/06/dita-170.sch" title="Schematron for DITA version 1.7.0">dita-170.sch</a></td>
</tr>
<tr>
<td>1.8.0</td>
<td>2008-07-16</td>
<td>Added tests for role attribute.</td>
<td><a href='/wp-content/uploads/2008/07/dita-180.sch' title="Schematron for DITA version 1.8.0">dita-180.sch</a></td>
</tr>
<tr>
<td>2.0.0</td>
<td>2008-12-18</td>
<td>Added 1.2 recommendations.</td>
<td><a href='/wp-content/uploads/2007/10/dita-200.sch' title="Schematron for DITA version 2.0.0">dita-200.sch</a></td>
</tr>
</table>

