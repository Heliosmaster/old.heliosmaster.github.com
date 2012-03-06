---
layout: post
title: "Visualizing commits"
tags: english
---

The recent boom of infographics is the proof that data visualization has become more and more important, and it is a useful tool to gain more insights.

Today, due to the launch of the revamped [Basecamp](http://basecamp.com/), and in particular to [its announcement](http://37signals.com/svn/posts/3128-basecamp-next-in-phases-and-flow) in 37signal's company blog, "Signal vs Noise", I discovered a fun tool to visualize data (namely, commits): **gource** (I guess that its name comes from _graphical source_ or something like that).

Such program is very easy to use and produces a interesting, _flowerish_ output. Since it is almost spring (the weather is not particularly agreeing with me in this matter, at least here in the Netherlands), I thought it deserved a post.

Anyway, after installing the required libraries (needless to say, I should have consulted the INSTALL file before trying to understand what was needed with a rule of thumb and the output of `./configure`), I managed to have it process the commit log of [tux.it](http://tux.it) and produce a nice HD video with this command:

`gource -1280x720 -s 4 -a 2 --hide dirnames,filenames --stop-at-end --title tux.it -o - | ffmpeg -y -r 60 -f image2pipe -vcodec ppm -i - -vcodec libx264 -vpre lossless_ultrafast -crf 1 -threads 0 -bf 0 ~/gource.mp4`

Luckily enough, I had just a little problem with ffmpeg and the encoding (that's why there is `-vpre lossless_ultrafast` instead of `preset ultrafast` or something like that, which was in the original suggestion from gource's wiki).

Anyway, here's the result:

<iframe width="640" height="360" src="http://www.youtube-nocookie.com/embed/t4_Rohdy0GA" frameborder="0"></iframe>


As a bonus to this post, I will add that I had some problems while trying to embed the video above: Maruku didn't like much the code that YouTube provided, but luckily I found [this tip](http://www.whatwherewhy.me/blog/2012/01/17/youtube-iframe-code-gotcha-in-maruku/), but then again, just after the iframe, the page stopped rendering (a known issue of maruku, as far as I understood), so I [looked a bit around](http://stackoverflow.com/questions/373002/better-ruby-markdown-interpreter) and switched to RDiscount. We'll see.