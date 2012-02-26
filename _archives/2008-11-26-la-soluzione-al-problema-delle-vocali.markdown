---
layout: post
title: La soluzione al problema delle vocali
wordpress_id: 1266
wordpress_url: http://blog.andvari.it/?p=1266
tags: italiano
date: 2008-11-26 11:28:02.000000000 +01:00
---
Qualche giorno fa <a href="http://blog.andvari.it/2008/11/20/aiuto-in-python/">avevo postato</a> del mio problema in Python. Che ho poi risolto semplicemente mettendomi in pari con la teoria e con un po' di immaginazione.

Il programma è il seguente, tutto in una riga:

<code>def f(a): return filter(lambda x: x not in 'aeiou',a)</code>

55 caratteri, puliti puliti.
