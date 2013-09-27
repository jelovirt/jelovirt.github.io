---
layout: post
title: Muuntaja Scala code generation
---
I've made some progress with Muuntaja, the Scala driven fork of DITA-OT. The only unimplemented basic features are Ant exec and custom DITA-OT tasks for HTMLHelp. Once those are done, I still have PDF2 to migrate and then I can start verifying that the generated code actually works in all cases. I haven't implemented PDF2 yet because currently the PDF2 Ant script simply imports XSL formatter specific Ant scripts and I'm not sure if that's the way I want to implement it in Scala. There aren't that many options, namely to either pass the XSL formatter as a parameter or to create each XSL formatter as a subclass of the main PDF2 class.

Right now the generated Scala code is chimera of coding styles and you can still clearly see it's been ported from Ant. I haven't decided whether to keep each processor class with functions (i.e. plain code) or whether to try and develop a DSL which would hide the details a bit. The plain code would make debugging easier and allow basically limitless extensibility. However, a DSL might make the code more readable as at this level the operations are quite simple: depend on something, set up properties, run XSLT for a set of files etc. A DSL is also something I've never written before, so it would be again something new. 

\#dita-ot #scala #muuntaja