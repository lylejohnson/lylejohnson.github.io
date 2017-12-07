---
id: 401
title: Installing Openfire on Ubuntu 10.04 LTS
date: 2010-12-02T18:20:04+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=401
permalink: /2010/12/02/installing-openfire-on-ubuntu-10-04-lts/
categories:
  - Software Development
---
When I officially [quit working on FXRuby](http://lylejohnson.name/blog/2010/08/04/moving-on/) back in August, one of the motivations was to give me more time to work on developing an idea that has been bouncing around in my head for quite awhile now. While I&#8217;m not yet ready to make an announcement about that, I will occasionally be writing here about some of the pieces of that app as I get around to implementing them. One such piece is an [XMPP](http://en.wikipedia.org/wiki/Extensible_Messaging_and_Presence_Protocol) (aka Jabber) server.

There seem to be a lot of XMPP servers out there, but two especially popular ones are the Java-based [Openfire](http://www.igniterealtime.org/projects/openfire/) and the Erlang-based [ejabberd](http://www.ejabberd.im/). ejabberd has a lot going for it and is used in a number of high-profile settings (most notably, as the basis of Facebook&#8217;s Chat service). Nevertheless, I&#8217;m more familiar with Java, and I don&#8217;t want to get too bogged down with the details of how the XMPP server works (i.e. that&#8217;s not the focus of this project), so I&#8217;ve decided to start out with Openfire. I did run into a few little problems while trying to get it up and running under Ubuntu 10.04 server, and so I thought I&#8217;d take a minute to write about that experience here.

My first step was to download the latest release of Openfire from the [downloads page](http://www.igniterealtime.org/downloads/). If you choose the &#8220;Linux&#8221; option on that page, you&#8217;ll be offered four different download package options. I chose the Debian package since I was installing on Ubuntu.

The first snag I ran into was that this Debian package has a dependency on the older &#8220;Sun&#8221; JRE packages (either `sun-java5-jre` or `sun-java6-jre`), which have more recently been replaced by the OpenJDK packages. Assuming you&#8217;ve already installed the OpenJDK package(s), you can work around this dependency by telling `dpkg` to ignore dependencies:

> <pre>dpkg -i --force-depends openfire_3.6.4_all.deb</pre>

The next snag was closely related to this, and has to do with the Openfire startup script that&#8217;s installed to `/etc/init.d`. The first bit of this script attempts to determine `JAVA_HOME`, but it does so by assuming that you&#8217;ll have one of the aforementioned Sun JRE packages installed. To work around this, modify this block of code so that it also checks for the OpenJDK as follows:

At this point you should be able to start the Openfire server by typing

> <pre>sudo /etc/init.d/openfire start</pre>

and then access its administrative console for further setup.