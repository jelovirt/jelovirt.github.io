---
layout: post
title: DITA-OT command line tool
---
Because I know I will not have time to write a proper announcement post, I'll just mention it here quickly: I started to work on DITA-OT version "next", basically DITA-OT 2.0. It will be backwards incompatible in some cases, but it will follow DITA-OT 1.x development for features implemented in the official project.

The first feature I'm rolling out is a new client tool, intended to replace the old Java command-line tool. It's not a finished tool, but rather just something I've started to work on, but the main feature there is that you no longer need to run startcmd.sh to configure the environment variables. Instead, you just have the command "dita". You probably want to add DITA-OTnext/bin directory to PATH variable, so that it will be always available, but you can also just run DITA-OTnext/bin/dita. Right now it's taking arguments in the Ant format, so you would use something like

    dita -Dargs.input=$HOME/temp/test.ditamap -Dtranstype=xhtml -Ddita.out=$HOME/temp

The reason for not having custom argument format yet is that I want to think about this and get feedback from people. So for now, you can think of this as running DITA-OT via Ant, except environment configuration is done automatically and you use the command "dita".

There are nightly binaries available at https://www.dropbox.com/sh/znkyu7rawgowa87/rEX8F97mXC so you don't need to build the packages yourself. If you find yourself testing the new tool, do let me know if there's something it should do differently.

\#dita-ot #dita-ot-next