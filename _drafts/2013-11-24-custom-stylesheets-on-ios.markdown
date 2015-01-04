---
layout: post
title: Custom stylesheets on iOS
---
<p>Today <a href="http://www.feynmanlectures.caltech.edu/">Caltech</a> published the <a href="http://www.feynmanlectures.caltech.edu/III_toc.html">third volume</a> of <a href="http://en.wikipedia.org/wiki/The_Feynman_Lectures_on_Physics">The Feynman Lectures</a> making me jump all around, not quite unlike when the <a href="http://www.feynmanlectures.caltech.edu/I_toc.html">first volume</a> became available. Having bought an iPad Air and <a href="https://twitter.com/gravicle/statuses/404408057134067712">loving it very much</a>, I use it for most of my reading and studying. Feynman lectures looked quite unappealing on the iPad curtesy of the persistent &#8220;Buy Now&#8221; menu floating in the right-top corner and the tiny font size. To rectify this, I started looking for a way to load custom stylesheets is Safari on the iPad. I tried using Provisioning Profiles but could not figure how to make them work. Then, I stumbled across <a href="http://juicystudio.com/article/accessible-stylesheet-bookmarklet.php">this tutorial</a> on Juicy Studio detailing the process of creating an accessibility stylesheet bookmarklet. It basically solved the issue for me. Here is a page from the HTML version of The Feynman Lectures before and after.</p>

<img src="http://spinhalf.net/wp-content/uploads/2013/11/fy1.jpg" width="100%" /></br>

<p>How to do it yourselves?</p>

<ul>
<li>Create a stylesheet, upload it to your hosting account and grab a direct link to the <code>.css</code> file.</li>
<li>Paste the link in place of <code>STYLESHEET-LINK-HERE</code> in the following JS</li>
</ul>

<p><code>javascript:(function()%7Bif%20(!document.getElementById(&#8216;someuniqueid&#8217;))%7Bvar%20objHead%20=%20document.getElementsByTagName(&#8216;head&#8217;);%20if%20(objHead%5B0%5D)%7Bif%20(document.createElementNS%20&amp;&amp;%20objHead%5B0%5D.tagName%20==%20&#8217;head&#8216;)%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElementNS(&#8216;http://www.w3.org/1999/xhtml&#8217;,%20&#8217;link&#8217;));%20else%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElement(&#8216;link&#8217;));%20objCSS.id%20=%20&#8217;someuniqueid&#8216;;%20objCSS.rel%20=%20&#8217;stylesheet&#8217;;%20objCSS.href%20=%20&#8217;STYLESHEET-LINK-HERE&#8216;;%20objCSS.type%20=%20&#8217;text/css&#8217;;%7D%7D%7D)()</code></p>

<ul>
<li>Create a bookmarklet with the given code. If you need help with this, <a href="http://www.youtube.com/watch?v=Jm1j9-lfw98">here is a helpful video</a>; except that you&#8217;ll erase the URL and paste the JS we just edited instead of editing the URL.</li>
<li>Place the bookmarklets in &#8220;Bookmarks&#8221;, i.e. on the top level. This will allow you quick access.</li>
</ul>

<p>Here is the bookmarklet I created for Feynman Lectures.</p>

<pre><code>javascript:(function()%7Bif%20(!document.getElementById('someuniqueid'))%7Bvar%20objHead%20=%20document.getElementsByTagName('head');%20if%20(objHead%5B0%5D)%7Bif%20(document.createElementNS%20&amp;&amp;%20objHead%5B0%5D.tagName%20==%20'head')%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElementNS('http://www.w3.org/1999/xhtml',%20'link'));%20else%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElement('link'));%20objCSS.id%20=%20'someuniqueid';%20objCSS.rel%20=%20'stylesheet';%20objCSS.href%20=%20'http://culturedpixel.com/custom-stylesheets/fy.css';%20objCSS.type%20=%20'text/css';%7D%7D%7D)()
</code></pre>

<p>Here is another with dark mode!</p>

<pre><code>javascript:(function()%7Bif%20(!document.getElementById('someuniqueid'))%7Bvar%20objHead%20=%20document.getElementsByTagName('head');%20if%20(objHead%5B0%5D)%7Bif%20(document.createElementNS%20&amp;&amp;%20objHead%5B0%5D.tagName%20==%20'head')%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElementNS('http://www.w3.org/1999/xhtml',%20'link'));%20else%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElement('link'));%20objCSS.id%20=%20'someuniqueid';%20objCSS.rel%20=%20'stylesheet';%20objCSS.href%20=%20'http://culturedpixel.com/custom-stylesheets/fy-dark.css';%20objCSS.type%20=%20'text/css';%7D%7D%7D)()
</code></pre>

<p>Here is one that I adapted from the <a href="https://github.com/gingerbeardman/Beautipedia.safariextension">Beautipedia Safari Extension</a>. It makes Wikipedia a bit better than the &#8220;Reader&#8221; view on the iPad and you don&#8217;t even have to go to another app.</p>

<pre><code>javascript:(function()%7Bif%20(!document.getElementById('someuniqueid'))%7Bvar%20objHead%20=%20document.getElementsByTagName('head');%20if%20(objHead%5B0%5D)%7Bif%20(document.createElementNS%20&amp;&amp;%20objHead%5B0%5D.tagName%20==%20'head')%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElementNS('http://www.w3.org/1999/xhtml',%20'link'));%20else%20var%20objCSS%20=%20objHead%5B0%5D.appendChild(document.createElement('link'));%20objCSS.id%20=%20'someuniqueid';%20objCSS.rel%20=%20'stylesheet';%20objCSS.href%20=%20'http://culturedpixel.com/custom-stylesheets/beautipedia/beautipedia.css';%20objCSS.type%20=%20'text/css';%7D%7D%7D)()
</code></pre>

<p>Before and after shots:</p>

<img src="http://spinhalf.net/wp-content/uploads/2013/11/wiki1.jpg" width="100%" /></br>
