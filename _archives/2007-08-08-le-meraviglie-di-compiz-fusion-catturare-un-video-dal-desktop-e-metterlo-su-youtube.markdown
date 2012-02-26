---
layout: post
title: Le meraviglie di Compiz Fusion + Catturare un video dal Desktop (e metterlo
  su Youtube)
wordpress_id: 88
wordpress_url: http://blog.andvari.it/2007/08/08/le-meraviglie-di-compiz-fusion-catturare-un-video-dal-desktop-e-metterlo-su-youtube/
tags: italiano
date: 2007-08-08 19:21:09.000000000 +02:00
---
Compiz Fusion è fantastico, per coloro che amano effetti di ottima qualità. E <a href="http://www.youtube.com/watch?v=lyuQUBSzTsU">il video che ho caricato su youtube</a>, lo dimostra.

Comunque in questo post non parlerò di quello che potete benissimo vedere da soli, ma di come riuscire a creare ed esportare in .avi (e magari caricare su Youtube).

$ sudo apt-get install recordMyDesktop gtk-recordMyDesktop (per chi vuole l'interfaccia grafica)

Applicazioni &gt; Audio &amp; Video &gt; gtk-recordMyDesktop

Iniziare a registrare. Premere nell'icona apparsa nella barra delle applicazioni (a forma di quadratino) per terminarla. Aspettare che venga salvato il file (di default è out.ogg nella cartella home)
<code>$ sudo apt-get install mencoder</code> se non ce l'avete già

<code>$ mencoder out.ogg -ovc  lavc out.avi</code>

ovviamente sostituite out.ogg e out.avi con il file sorgente e il file di destinazione.

Attendere che il programma finisca, et voilà.
