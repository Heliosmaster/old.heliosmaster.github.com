---
layout: post
title: "Re-encode a website into UTF-8"
tags: english
---

Over at [Bifrost.it](http://bifrost.it), we care much about using the right characters when spelling a word, particularly if they are not particularly common.

So, it is quite understandable (actually, I can't find a better example where this should be applied to), that every HTML page of the site has to be encoded in UTF-8. 

Unluckily, until a few days ago, it was not the case: mostly because the building of that pages is done under Windows (with FrontPage (sic)), the encoding were a mixed of ISO-8859-1 and Windows-1252 (which showed up as `unknown-8bit`).

So, we needed to do the following:

1. Check which encoding had a page, and convert from that to UTF-8
2. Insert the HTML meta tag `<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\"/>`

For point 1, I basically used `file` and `iconv` inside a ruby script, whereas for point 2 I took advantage of the fact that the pages were written with FrontPage, which dirties the code a lot with its own crap, and so I simply performed a find& replace on one of this useless things it adds.

The ruby script to obtain all is the (more or less) following:

<script src="https://gist.github.com/2517777.js"> </script>