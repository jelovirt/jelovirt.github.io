---
layout: post
title: Benefits of parallel processing
---
Checking how DITA-OT would benefit from parallel processing. Changing keyref write processing to be run in multiple threads, the results for module execution times are:

- 1 thread: 162 sec
- 2 threads: 124 sec
- 3 threads: 117 sec
- 4 threads: 112 sec
- 5 threads: 114 sec
- 6 threads: 112 sec
- 7 threads: 111 sec
- 8 threads: 107 sec

(Test document is part of DITA 1.2 spec, on a 4 core processor with hyper-threading; only one test run)

I haven't checked how the memory consumption will grow, but it's not too bad for keyref processing. I Implemented the parallelization with java.util.concurrent.ExecutorService and the resulting code is pretty easy to read. If I add the parallel processing enhancements to DITA-OT core, the default will be the old single thread processing.

\#dita-ot