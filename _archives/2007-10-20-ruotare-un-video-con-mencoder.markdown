---
layout: post
title: Ruotare un video con mencoder
wordpress_id: 38
wordpress_url: http://blog.andvari.it/2007/10/20/ruotare-un-video-con-mencoder/
tags: italiano
date: 2007-10-20 20:08:32.000000000 +02:00
---
Ogni tanto scrivo quando mi devo ricordare di un'operazione che ho fatto, e la pubblico così può essere utile anche a qualcun altro:
<blockquote><code>mencoder -vf rotate=1 -ovc lavc -oac copy source.avi -o destination.avi</code></blockquote>
<ul>
	<li>0    Rotate by 90 degrees clockwise and flip (default).</li>
	<li>1    Rotate by 90 degrees clockwise.</li>
	<li>2    Rotate by 90 degrees counterclockwise.</li>
	<li>3    Rotate by 90 degrees counterclockwise and flip.</li>
</ul>
