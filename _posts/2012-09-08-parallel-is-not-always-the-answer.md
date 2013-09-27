---
layout: post
title: Parallel is not always the answer
---
Dug out https://github.com/jelovirt/dita-ot/tree/parallel and merged in the latest code from the main repo. I didn't expect to get different results than before, but it was still somewhat disappointing to see that the parallelization in DITA-OT gives very little performance boost; the I/O will always be the bottle neck.

I'm not sure which alternative approach to performance I should start investigating. The two I've been considering are:

1. Combine as many of the pipeline module calls to a single call, so that files are piped through multiple modules and a single file is parsed and serialized only once.

2. For smaller sets, retain files in memory through out the whole preprocessing phase. I would much rather use XOM than DOM, and Saxon already has JAVAX Source and Result implementations for XOM, but it's probably easier to just go with DOM. If the storage backend was pluggable, an implementation which used an XML database could also be used. (Haven't a clue if this would actually improve performance, but it would be fun to code.)

I think the former would be a better place to start, and then continue with the latter one. 

\#dita-ot