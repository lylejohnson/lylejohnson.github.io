---
id: 200
title: Distributed Source Control Systems
date: 2007-05-18T21:14:11+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=200
permalink: /2007/05/18/distributed-source-control-systems/
categories:
  - Software Development
---
Kyle Cordes&#8217; recent [post](http://kylecordes.com/2007/05/17/linux-git-distributed/ "Linus Torvalds explains distributed source control") about distributed source control reminded me that learning more about that topic has been on my Someday/Maybe list for awhile now. It&#8217;s Kyle&#8217;s opinion that distributed source control systems are &#8220;dramatically better&#8221; than centralized systems (like Subversion). I still haven&#8217;t decided whether distributed source control is a solution to a problem that I don&#8217;t have, but the bits about it making creating and merging branches easier appeal to me, so I decided to dig a little deeper.

All of the projects that I work on use Subversion as their source control system, so I needed to find something that would play nice with it. [SVK](http://svk.bestpractical.com/view/HomePage "SVK Home Page") seemed like an obvious choice since it&#8217;s layered on top of Subversion, and there&#8217;s a port for it in MacPorts, so that&#8217;s where I started. After I got the software installed, I worked through Ron Bieber&#8217;s excellent [tutorial](http://www.bieberlabs.com/wordpress/archives/2004/11/30/using-svk "SVK - Distributed Version Control - Part I") series to get a feel for the SVK workflow. I highly recommend these tutorials if you&#8217;re considering using SVK.

I&#8217;ve been experimenting with SVK for a couple of days now, primarily doing some development on the FXRuby 1.6 branch, and it was working like a charm. I have to admit that it&#8217;s a little slow, especially considering that it&#8217;s just looking at stuff on the local disk. But it seemed to be working. Unfortunately, I just discovered that SVK doesn&#8217;t support the `svn:externals` property. That is, if a directory in your Subversion repository has the `svn:externals` property set on it, SVK will not properly mirror those external directories (it just ignores them). This isn&#8217;t an issue for the FXRuby repository, but many of the other projects that I work on make at least some use of Subversion externals. For the time being, that means no SVK for me.

So, back to the drawing board. I know of several alternatives that I can look at, like [git](http://git.or.cz/ "Git Home Page"), [Mercurial](http://www.selenic.com/mercurial/wiki/ "Mercurial Home Page"), [Bazaar](http://bazaar-vcs.org/ "Bazaar Home Page") and [arch](http://www.gnu.org/software/gnu-arch/ "Arch Home Page"). The main requirement for me is that it works on Mac OS X, and that it plays nice with Subversion (i.e. it can both pull down the latest changes from a Subversion repository and push my changes back to that repository). And, um, it has to support `svn:externals`. Any suggestions?

**Update:** Looks like people are also talking about [Monotone](http://monotone.ca/ "Monotone Home Page") and [darcs](http://www.abridgegame.org/darcs/ "darcs Home Page"). Meanwhile, at first glance it doesn&#8217;t sound like git supports svn:externals either. I&#8217;m getting a sinking feeling that none of &#8216;em will. Oh well, we&#8217;ll see.