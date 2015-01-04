---
layout: post
title: Sounds in Alfred Workflows
date: 2013-05-28 08:48:29.000000000 -05:00
---
<p>Today I was working on an Alfred workflow to clear my desktop and realized that a sound notification would suit it much better than the Notification Center notification I was using. My workflows are mostly all AppleScripts. So the question was:</p>

<p><strong>How to play sounds within AppleScripts?</strong></p>

<p>Looking around on the internet, I stumbled across this Dr. Drang <a href="http://www.leancrew.com/all-this/2007/12/playing-sounds-in-applescript/">post</a>. He uses <a href="http://microcosmsoftware.com/playsound/">Play Sound</a> for its AppleScript dictionary to, well, play sounds. </p>

<pre><code>tell application &quot;Play Sound&quot;
    play &quot;HD:System:Library:Sounds:Glass.aiff&quot; repeat 1
end tell
</code></pre>

<p>However, in the comments &#8220;tsinn&#8221; suggested using <code>afplay</code>.</p>

<blockquote>
<p>use afplay eg: do shell script “afplay /System/Library/Sounds/Submarine.aiff”</p>
</blockquote>

<p>And this is where I start.</p>

<h3>Shell Scripts and Sounds in Alfred</h3>

<p>You can use shell scripts to execute terminal commands without popping open the terminal window. From within an AppleScript, you can execute a shell script with:</p>

<pre><code>do shell script &quot;--your command here--&quot;
</code></pre>

<p>For playing sounds, I am using OS X&#8217;s built in command-line audio player, <code>afplay</code><a href="#fn:1" id="fnref:1" title="see footnote" class="footnote">[1]</a>. You can also find system sounds in <code>/System/Library/Sounds</code> and even more in <code>/System/Library/Components/CoreAudio.component/Contents/Resources/SystemSounds</code>. I copied all of these to my &#8220;Alfred-Resources&#8221; folder in Dropbox and added quite a few more from around the web<a href="#fn:2" id="fnref:2" title="see footnote" class="footnote">[2]</a>. With sound-files at hand, all it takes to play them from within AppleScripts in Alfred workflows is this shell script:</p>

<pre><code>do shell script &quot;afplay {path to the sound file}&quot;
</code></pre>

<p>For example, to use the pop system sound<a href="#fn:3" id="fnref:3" title="see footnote" class="footnote">[3]</a>:</p>

<pre><code>do shell script &quot;afplay /System/Library/Sounds/Pop.aiff&quot;
</code></pre>

<p>That&#8217;s it!</p>

<p>Also, <a href="http://spinhalf.net/wp-content/uploads/2013/05/Link-Workflows-for-Alfred.zip">here →</a> is a goody bag with two of my most used extensions for link handling (in Safari and Chrome flavors):</p>

<ol>
<li>Fetch Safari URL: It retrieves the URL of the front-most tab in Safari, copies it to clipboard as well as pastes it if there is a text-field in focus and finally, leaves a space for you to keep writing. There is another very lovely easter egg in the workflow for ByWord users. Go hunting :)</li>
<li>Tweet link from Safari: It retrieves the URL and the title of the front-most tab in Safari, creates a new tweet in Tweetbot and pastes the title followed by the URL. Then, it goes to the beginning of the tweet, presses ↩ twice, goes to top again and gives you a place to write. If you don&#8217;t add any comments, Twitter simply ignores the line breaks.</li>
</ol>

<p>Tip: I refrain from using hotkeys (keyboard shortcuts) in Alfred. But if you see some in these workflows, it is because I found a hotkey to be the most efficient way of accomplishing the task. Try using them (you&#8217;ve to set them first) instead of the keywords.</p>

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
<p>You can find out more about <code>afplay</code> from Terminal using <code>afplay -h</code> <a href="#fnref:1" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:2">
<p>There are tons of .aiff sounds repositories on the web. This <a href="http://stackoverflow.com/questions/167617/where-do-you-get-your-application-sounds-from">SE page</a> has a great list. <a href="#fnref:2" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

<li id="fn:3">
<p>I much prefer &#8220;Ink Sound Become Mouse.aif&#8221; in <code>/System/Library/Components/CoreAudio.component/Contents/Resources/SystemSounds/ink</code>. <a href="#fnref:3" title="return to article" class="reversefootnote">&#160;&#8617;</a></p>
</li>

</ol>
</div>
