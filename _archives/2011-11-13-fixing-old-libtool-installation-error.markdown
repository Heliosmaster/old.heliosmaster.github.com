---
layout: post
title: Fixing old libtool installation error
wordpress_id: 1996
wordpress_url: http://blog.andvari.it/?p=1996
tags: english
date: 2011-11-13 12:03:12.000000000 +01:00
---
Since lately I've been using this blog just as a pinboard for useful stuff, today I will share something with my readership (and more importantly, google's spiders)

I tried to install the <em>dieharder</em> test suite in order to perform some tests on Random Number Generators for a report I am writing, and I stumbled upon this issue:

<pre>
libtool: Version mismatch error. This is libtool 2.2.10, but the libtool: definition of this
         LT_INIT comes from an older release.
libtool: You should recreate aclocal.m4 with macros from libtool 2.2.10
libtool: and run autoconf again.
</pre>

After a quick googling, I have been able to solve it running these commands:

<pre>
aclocal
libtoolize --force
autoheader
autoconf
./configure
make
</pre>
