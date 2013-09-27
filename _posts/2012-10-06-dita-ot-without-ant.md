---
layout: post
title: DITA-OT without Ant
---
I don't really remember when I came up with the idea that I could write some code to convert DITA-OT's Ant files into Python. Back then I thought I could use Jython to then run those Python classes and I would have a more direct access to DITA-OT's modules and other classes. That worked out, I was able to run e.g. an XHTML transformation. The approach I took was to convert the integrated build.xml into a Python file where each Ant import created a Python object.

Few weeks ago I continued with the experiment and modified the Python generation code to generate Groovy instead. This was partially motivated because I wanted to see what the language was like and because Groovy is very similar to Python in this case and it was easy. However, Groovy didn't feel interesting for some reason, so I though I would take the direction I had been planning back in the beginning: generate Scala code instead. The reasons for choosing Scala and reason for the whole project really are:

* Ant is not a programming language and it lacks even the most simple control structures
* Ant Project has no way of storing custom objects, such as the Job object
* The driver code should not just be configuration, but something you can program in
* Scala runs on the JVM, so you can directly interact with DITA-OT's Java code
* Scala can be made terse and is quite lovely
* Scala has support for running scripts which may be handy for people who are used to being able to write configuration and not compile anything

It's been a couple of years since I really wrote Scala code for toy projects, so I dug out "Programming in Scala" and started to modify the existing XSLT code. I made few changes to the generation:

* generate multiple files, one for each class
* generate code from transtype specific post-integration Ant files, not from build.xml
* have all transtypes inherit from Transtype class and then Preprocess class
* remove indentation because Scala doesn't require it, and use Eclipse to format the code if needed
* add Ant target inlining for e.g. \*-check targets which are last in the dependency chain for a given target
* replace using list files with directly accessing the Job object

The results are at https://github.com/jelovirt/dita-ot/tree/python/src/main/scala/org/dita/dost/module. Nothing too special, but it's a fun toy project. PDF2 hasn't been implemented yet because I haven't made up my mind how to handle support for different XSL formatters in the code. The processing still apes Ant, in that is uses a global properties and a function dependency chain, but I will need to move some of the global properties into instance variables and possibly try and clean the dependency system a bit. The code is still generated from Ant files, so any clean-up I make in the core DITA-OT Ant files will be available to Scala version. The reason I still want to improve the generation is that I want the Scala code to look pretty and be easy to read. That way I might be able to actually make something out of this, to have "Scala DITA-OT" be a product which could be used in production.

At some point, I would probably need to stop the code generation and start developing the Scala code as the normative source. But, as long as I can, I will keep the Ant as the source and just add code rewrites into the generation. Not sure what the next step will be, maybe reimplementing the ExtensibleAntInvoker in Scala, so that I can generate module calls which look more Scala-like.

Maybe I should reuse the name of an old toy project for a DITA processor in Scala to rebrand this fork of DITA-OT: Muuntaja.

\#scala  #dita -ot