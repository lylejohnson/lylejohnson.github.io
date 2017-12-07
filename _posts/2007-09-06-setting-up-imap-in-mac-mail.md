---
id: 227
title: Setting up IMAP in Mac Mail
date: 2007-09-06T20:28:44+00:00
author: Lyle
layout: post
guid: http://lylejohnson.name/blog/?p=227
permalink: /2007/09/06/setting-up-imap-in-mac-mail/
categories:
  - Apple
---
After Steve&#8217;s [announcement](http://www.macrumors.com/2007/09/05/8gb-iphone-price-drop-4gb-iphone-discontinued/ "8GB iPhone Price Drop, 4GB iPhone Discontinued") yesterday of the iPhone price drop, I finally gave in and bought the last 8Gb model the local AT&T store had in stock. After the initial sync from iTunes, the next order of business was to get Wi-Fi and Mail working.

My first attempt was to just POP into my existing Gmail account. Technically speaking, this worked fine, but it had the undesirable effect of downloading a lot of old e-mail messages that I thought were ancient history. This wouldn&#8217;t be so bad if it weren&#8217;t for the fact that the iPhone Mail application doesn&#8217;t have a way to clear out all of your deleted messages. You have to go in and [delete them one-by-one](http://www.macworld.com/2007/07/firstlooks/iphone_wishlist/index.php "Macworld: iPhone fixes we want to see"). Yes, seriously.

Even if I ironed out the short-term problem of downloading already-archived Gmail messages, I was worried that this wouldn&#8217;t be a workable solution moving forward. So, after doing some research here and there I decided that what I needed was an IMAP account. I&#8217;d heard of IMAP before, obviously, but for whatever reason I&#8217;ve just never used it. Luckily, [my hosting provider](http://www.asmallorange.com/ "A Small Orange") supports both POP and IMAP accounts, so I set up one for myself and told Gmail to start forwarding all of its incoming messages to that account. And this part worked like a charm. The same sources recommended that I get my Mac Mail client talking to this IMAP account first, before trying to get it set up on the iPhone. Fair enough &#8212; how hard could _that_ be?

Actually adding the account in Mail went pretty smoothly. I had the names of the incoming and outgoing mail servers, as well as my user name and password. When I finished adding the account, Mail verified that it could connect to the IMAP server and that went fine. I observed that it synchronized with the IMAP server and created &#8220;Drafts&#8221;, &#8220;Sent&#8221; and &#8220;Trash&#8221; mailboxes under my standard Inbox, which at the time seemed like a reasonable thing to do. I could even see that the messages that Gmail had forwarded to the IMAP account were there in my Inbox now.

The problem that I started running into was that when I tried to compose a new e-mail message in Mail, and save a draft of it, Mail would pop up a dialog box with a cryptic error message: &#8220;The message could not be saved&#8221;. No indication why it couldn&#8217;t be saved, or what I could do to correct that problem. I also discovered soon after that I couldn&#8217;t send e-mail messages. When I tried to send messages, I didn&#8217;t even get an error dialog; the messages just disappeared into the ether.

So I started doing some more research online, and quickly discovered that I wasn&#8217;t the first person to run into this problem. The general consensus was that Mail&#8217;s support for IMAP is a little flaky, but several people offered their solutions and workarounds. One of the necessary steps is to tell Mail that the [IMAP path prefix](http://www.inertramblings.com/2006/03/09/mailapp-and-courier-imap-the-message-could-not-be-saved/) is &#8220;INBOX&#8221;; the other necessary step is to [set up a mapping](http://www.whatdoiknow.org/archives/002420.shtml) between the remote &#8220;Drafts&#8221;, &#8220;Sent&#8221; and &#8220;Trash&#8221; folders to the same folders in Mail.

The part that I got wrong was the order of these two steps, and to make a long story short, it apparently matters. If you define the IMAP path prefix first, it doesn&#8217;t seem to work properly. In my case, the &#8220;Drafts&#8221; folder would just disappear altogether with no way to get back to it. So wait to do that _after_ you&#8217;ve set up the mappings. It took me most of the day to get this working, but it does seem to be OK now.