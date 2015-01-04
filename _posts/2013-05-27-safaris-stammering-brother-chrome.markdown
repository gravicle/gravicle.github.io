---
layout: post
title: 'Safari''s Stammering Brother: Chrome'
date: 2013-05-27 12:38:15.000000000 -05:00
---
<p>This is not another why you should use {insert browser name here} post. Instead it is a log of my experiences as I tried switching to Chrome from Safari.</p>

<p>I have been an avid Safari user and like the browser for most part. However, it has its quirks. Most noticeable is its grind as the number of tabs increase. Chrome, on the other hand, is known to be extremely fast and particularly deft at juggling tabs, many many of them. So, I decided to give it a spin, again. Here are the specifics of the experiment:</p>

<ul>
<li><strong>Machine</strong>: MackBook Pro with Retina Display, mid 2012.

<ul>
<li>Processor: 2.3 GHz Intel Core i7</li>
<li>RAM: 8 (2x4GB) GB 1600 MHz DDR3</li>
<li>Graphics: Intel HD Graphics 4000 512 MB / NVIDIA GeForce GT 650M 1024 MB</li>
<li>Display Resolution 1440x900 2x scaled (Retina)</li>
<li>Storage: Samsung SM256E 256GB SSD (400mbps read/write)</li>
</ul></li>
<li><strong>OS</strong>: OS X 10.8.3</li>
<li><strong>Chrome</strong>: 27.0.1453.93 (Stable)</li>
<li><strong>Safari</strong>: 6.0.4 (8536.29.13)</li>
</ul>

<h3>Gripes with Safari</h3>

<p>The single most important reason to move away from Safari was it&#8217;s abysmal performance under heavy load. I have 20&#8211;30 tabs open at a time<a href="#fn:1" id="fnref:1" title="see footnote" class="footnote">[1]</a>. Some tabs might have a video and thus, flash. Safari just halts to a grind even on such a powerful machine.</p>

<h3>Chrome</h3>

<p>There were quite a few things that ticked me off about Chrome. All of this is definitely influenced by Safari and one could argue that I am being hysterical in expecting Chrome to have similar conventions as Safari. Again, these are <strong>my</strong> issues as a switcher and might not apply to you. You might be a better switcher than I am or coming from Chrome side of things. </p>

<ul>
<li><p>Safari assigns <strong>keyboard shortcuts</strong>, conforming to the pattern ⌘+{number}, to first 9 bookmarks in the bookmarks bar. This is incredibly handy and my default method of sending things to Pinboard and Instapaper. Chrome doesn&#8217;t do so. I found extensions which provide alternate launchers but none that could replicate the functionality. I also tried to set up <a href="http://5typos.net/post/6611916064/keyboard-shortcuts-for-bookmarklet-on-google-Chrome">custom keyboard shortcuts</a> that&#8217;d activate the bookmarklets. However, there is a bug in Chrome that would not let this happen. Then I resorted to creating an <a href="https://www.dropbox.com/s/6bmbx5afy71ohsw/Chrome%20Bookmarks.alfredworkflow?v=1mci">Alfred workflow</a> with GUI scripting to simulate mouse clicks. Federico Viticci has done <a href="http://www.macstories.net/links/launch-Chrome-bookmarklets-with-keyboard-shortcuts/">something similar</a> as well. This sort of addressed the issue. However, there is no automatic updating of shortcuts if the bookmarklets change.</p></li>
<li><p><strong>Smart Zoom</strong>: Safari, like its iOS counterpart, has smart zoom. Double clicking on an element (text, images etc) with 2 fingers zooms the element, and very elegantly so. Chrome, not so much. The only way to zoom is to use finger-pinching gesture and the result is extremely stuttery. To add to the disgrace, the zoom is applied to every single tab. It&#8217;s a jarring experience. Now, there are <a href="https://Chrome.google.com/webstore/detail/smooth-gestures/lfkgmnnajiljnolcgolmmgnecgldgeld?hl=en">some</a> <a href="https://Chrome.google.com/webstore/detail/dblclickzoomin/flcpghpdcjpneanjmojaimmmghnoondg?utm_source=Chrome-ntp-icon">extensions</a> which emulate Safari but do so horribly.</p></li>
<li><p><strong>Scrolling and page loading</strong>: Chrome is really fast at loading pages. No doubt. Opening new pages is considerably faster, tabs open quicker and this gives everything a snappy appeal. It beats Safari almost every time and does so noticeably. However, everything appears to be so discreet and rushed. There is no sense of physics to animations. To keep up with scrolling, Chrome would rather skip frames than slow down the scroll. Safari does things the exact opposite way. The result is no less choppy. While loading content, both browsers balk at scrolling but do great otherwise. </p></li>
<li><p><strong>iCloud sync</strong>: It&#8217;s a no brainer. I use Safari on iOS and thus, loose all sync functions with Chrome. Just an ecosystem issue.</p></li>
<li><p><strong>Top-sites</strong>: I never liked the idea of setting a home page for a browser. It&#8217;s a massive waste of time and the probability of me requiring to visit that page every single time I open a new tab/window is practically 0. Safari&#8217;s &#8220;Top Sites&#8221; is a great use of that new-tab space. It&#8217;s intelligent and adapts to my use. Chrome, on the other hand, offers a terrible clone and really stupid &#8220;apps&#8221; screen(s). Sincerely, I did not find a single &#8220;app&#8221; that I would want to use. It might be <em>an</em> idea for Chrome OS but for Chrome, it seems worthless.</p></li>
<li><p><strong>Omni-bar</strong>: Chrome introduced the omni-bar to browsers and I adore it. I was giddy like a little girl when Safari 6 finally shipped with one. However, there are nuances to their implementations. While Safari&#8217;s omnibar <a href="http://spinhalf.net/?attachment_id=546">prioritizes history and bookmarks</a>, <a href="http://spinhalf.net/?attachment_id=545">Chrome&#8217;s does Google suggestive search</a>. In Safari, I enter the first few letters of the name of the site and hit ↩ to be directed to the page I was looking for. It works surprisingly well. Chrome, on the other hand, takes me to Google search results. It is incredibly frustrating. While it is easy to understand the motivation behind the difference, it&#8217;s not a user-centric approach. It adds an extra step between me and the page I am gunning for. </p></li>
</ul>

<p>All these little things significantly altered my browsing experience. I always felt a little jarred in Chrome while most of the other apps on my Mac would work so elegantly and with finesse. This broke something.</p>

<h3>The thing I love about Chrome</h3>

<p><strong>Performance</strong>. And I am not even talking of page loading. I am referring to app performance: ability to handle more than 10 tabs without slowing down, launching new tabs and windows faster and not killing every single tab when one becomes unresponsive<a href="#fn:2" id="fnref:2" title="see footnote" class="footnote">[2]</a>.</p>

<h3>Designing browsers</h3>

<p>There is nothing simple about making browsers. Web rendering engines have to parse code written by more people in more ways than any other technology and have to be ridiculously fast and resource-constraint while doing so. Rapid iteration and dedicated focus has given Chrome an edge of Safari, so much so that now Safari is allegedly holding Chrome back. At least, that is the justification for the existence of Google&#8217;s Blink rendering engine, a Webkit fork.</p>

<p>Nonetheless, browsers are apps. In fact, they are the most used apps on almost any computer today. They are not exempt from the rules of HIGs and user interactions. Apple certainly excels at that and it shows in Safari. Nothing jumps out of place. There is nothing sudden about it. While for Chrome, the focus seems to be on speed and superfluous &#8220;features&#8221;. Maybe it will come around, but as of today, it is a junky browser.</p>

<p>After a week, I moved back to Safari today.</p>

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
<p>I am not generally lazy with tabs or even a tab-junky. It is just an organic outcome of my workflow while developing websites.  <a href="#fnref:1" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:2">
<p>I realize that this is a consequence of Apple&#8217;s insistence upon using a single process for all the tabs versus Chrome&#8217;s process-tab parity architecture. Apple is wrong here and should adopt Chrome&#8217;s model in future releases (OS X 10.9?). <a href="#fnref:2" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

</ol>
</div>
