---
layout: post
title: A Primer on Messages.app
date: 2013-05-05 16:39:36.000000000 -05:00
---
<p>This morning I finally got around to looking into my grievances with Messages.app. It is one of the few always-on apps on my Mac, besides Tweetbot, Reeder and a tiny collection of menu-bar utilities. Here, I am listing some ways to make Messages.app work better, especially if you like doing things with your keyboard.</p>

<h3>Keyboard Shortcuts</h3>

<p>Besides some of the standard OS-wide shortcuts, Messages.app features some handy others:</p>

<ul>
<li>Cycle thru conversations: <strong>⌘+[</strong> or <strong>⌘+]</strong>.
This is something I need to do very frequently, and I hate shortcuts with square brackets for being unintuitive<a href="#fn:1" id="fnref:1" title="see footnote" class="footnote">[1]</a>. So, I created custom keybindings to accomplish moving thru conversations. <a href="http://spinhalf.net/wp-content/uploads/2013/05/Screen_Shot_2013-05-05_at_7.09.59_PM.png">Here</a> is a skitch edit showing how to do so. I chose <strong>⌘+⌥+↑</strong> and <strong>⌘+⌥+↓</strong> for this<a href="#fn:2" id="fnref:2" title="see footnote" class="footnote">[2]</a>.
There is also a great Alfred Workflow to help you jump to any conversation with a keyword and buddy name. Find it <a href="http://www.alfredforum.com/topic/1168-imessage-focus-with-part-of-namehandle/">here→</a>.</li>
<li>Insert a new line: <strong>⌥+return</strong></li>
<li>Insert emojis using OS X&#8217;s built in Characters palette: <strong>⌥+⌘+T</strong></li>
<li>Insert previously sent messages: <strong>⌥+↑</strong> or <strong>⌥+↓</strong> with focus on text-field.</li>
<li>Scroll to top: <strong>⌘+↑</strong> with focus off the text-field.</li>
<li>Mark the conversation with a timestamp: <strong>⇧+⌘+K</strong></li>
<li>Send a file: <strong>⌥+⌘+F</strong></li>
<li>See file transfer status: <strong>⌥+⌘+L</strong></li>
<li>Search thru all messages: <strong>⌘+F</strong>. Be vary of significant beach-balling and CPU usage if your messages archive is huge (3.8GB for me).</li>
</ul>

<h3>Memory Leaks</h3>

<p>Messages.app has quite a few memory leaks, particularly in IMTransferAgent. It is generally active during file transfers and quits once all of them are done. If you find yourselves not receiving files after a normal wait, try killing the IMTransferAgent process in Activity Monitor.</p>

<p>Another easy way to address memory leaks is to restart the app periodically. At times, Messages can start consuming a lot of CPU cycles for no apparent reason. That&#8217;s when you know that it&#8217;s time to take the dog out in the woods.</p>

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
<p>My memory isn&#8217;t geared towards remembering keyboard shortcuts. The reason I prefer Alfred over Keyboard Maestro, which would be faster for obvious reasons, is that there is no way for me to memorize more than a few shortcuts. So, when I do resort to a custom shortcut, I want it to be intuitive. Using arrows to move between tabs is just such a no-brainer. <a href="#fnref:1" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:2">
<p>In fact, I am using the ⌥+⌘+{arrow} combination across any app where I move between tabs a lot. Like Safari, where I use <strong>⌘+⌥+→</strong> and <strong>⌘+⌥+←</strong>. <a href="#fnref:2" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

</ol>
</div>
