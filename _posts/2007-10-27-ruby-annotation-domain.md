---
title: "Ruby Annotation Domain for DITA 1.1"
layout: post
tags: dita dita domain-specialization ruby-annotation
---
<div class="note">
<strong class="note-title">Note: </strong>W3C has dealt with this in [W3C Best Practices for XML Internationalization](http://www.w3.org/TR/2008/NOTE-xml-i18n-bp-20080213/#its-dita).
</div>

A [DITA 1.1](http://www.oasis-open.org/committees/tc_home.php?wg_abbrev=dita) domain specialization of <tt>ph</tt> element. The element naming and content models follows [Ruby Annotation](http://www.w3.org/TR/ruby/) and [Internationalization Tag Set](http://www.w3.org/TR/its/), with the exception of

<ul>
	<li>omission of <tt>rbspan</tt> attribute from <tt>rt</tt> element.</li>
</ul>

See DTD files for details.

Download <a href="/wp-content/uploads/2007/12/rubydomain_111tar.gz" title="Ruby Annotation domain version 1.1.1">latest version</a>.
<!--more-->
<h3>Example</h3>
<pre>&lt;!DOCTYPE i18n_concept
  PUBLIC "-//ELOVIRTA.COM//DTD DITA I18N Concept//EN"
         "i18n_concept.dtd"&gt;&lt;i18n_concept id="ruby"&gt;
  &lt;title&gt;Ruby test&lt;/title&gt;
  &lt;conbody&gt;
    &lt;p&gt;W3C Associate Chairman, &lt;ruby xml:lang="ja"&gt;
        &lt;rbc&gt;
          &lt;rb&gt;斎&lt;/rb&gt;&lt;rb&gt;藤&lt;/rb&gt;&lt;rb&gt;信&lt;/rb&gt;&lt;rb&gt;男&lt;/rb&gt;
        &lt;/rbc&gt;
        &lt;rtc&gt;
          &lt;rt&gt;さい&lt;/rt&gt;&lt;rt&gt;とう&lt;/rt&gt;&lt;rt&gt;のぶ&lt;/rt&gt;&lt;rt&gt;お&lt;/rt&gt;
        &lt;/rtc&gt;
      &lt;/ruby&gt;&lt;/p&gt;
  &lt;/conbody&gt;
&lt;/i18n_concept&gt;</pre>
<h3>Change History</h3>
<table border="1">
<tr>
<th>Version</th>
<th>Date</th>
<th>Description</th>
<th>Download</th>
</tr>
<tr>
<td>1.0.0</td>
<td>2007-03-21</td>
<td>Initial release.</td>
<td>unavailable</td>
</tr>
<tr>
<td>1.1.0</td>
<td>2007-04-11</td>
<td>Moved elements to ITS namespace.</td>
<td><a href="/wp-content/uploads/2007/10/rubydomain_110tar.gz" title="Ruby Annotation domain 1.1.0">rubydomain_110tar.gz</a></td>
</tr>
<tr>
<td></td>
<td>2007-09-17</td>
<td>Changed the DITA base to version 1.1 without changes.</td>
<td></td>
</tr>
<tr>
<td>1.1.1</td>
<td>2007-12-09</td>
<td>Clarified licensing.</td>
<td><a href='/wp-content/uploads/2007/12/rubydomain_111tar.gz' title='Ruby Annotation domain version 1.1.1'>rubydomain_111tar.gz</a></td>
</tr>
</table>

