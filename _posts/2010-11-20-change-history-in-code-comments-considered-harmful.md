---
title: "Change history in code comments considered harmful"
layout: post
tags: programming rant
---
<img src="http://www.elovirta.com/wp-content/uploads/2010/11/x-l-150x150.gif" alt="" title="Harmful" width="150" height="150" class="alignright size-thumbnail wp-image-1090" />
		  
I really dislike seeing code comments that say

<pre>
// Changed by <var>X</var> on date <var>Y</var> for bug <var>Z</var> start
...
// Changed by <var>X</var> on date <var>Y</var> for bug <var>Z</var> end
</pre>

That is what [revision control](http://en.wikipedia.org/wiki/Revision_control) is for. Use commit messages that describe the reason for the change and generally make commits that change only one thing at a time. That's my preference over change history in code comments.

