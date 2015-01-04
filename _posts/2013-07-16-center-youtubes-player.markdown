---
layout: post
title: Center Youtube's Player
date: 2013-07-16 20:40:08.000000000 -05:00
---
<p>Youtube's wide player has always bugged me. Placed in the extreme left, it just looks erratic. I recently discovered that there exists a <a href="http://code.grid.in.th">User CSS plugin</a> for Safari and have been on a spree fixing minor style annoyances across the interweb. Here is the fix for the Youtube player:
<code></p>

<h1>player-api {</h1>

<p>margin-left: auto !important;
margin-right: auto !important;}
.watch-medium {
padding-left: 0px !important;
margin-top: 19px !important;
margin-bottom: 50px !important;}
.watch-sidebar {
margin-top: 0px !important;}</code>
The affected URL is: <code>http://<em>.youtube.com/</em></code></p>

<p>Before enabling the CSS, make the player wide. As an added bonus, the player will now always stay wide and centered. It looks much better this way.</p>

<p><img class="aligncenter size-large wp-image-602" alt="Screen Shot 2013-07-17 at 1.21.09 AM" src="http://res.cloudinary.com/daectagjz/image/upload/h_611,w_780/v1412562526/Screen-Shot-2013-07-17-at-1_21_09-AM_surwsg.png" width="780" height="610" /></p>
