---
layout: post
title: ! 'L''arte di arrangiarsi: Circuiti, PostScript e PNG'
wordpress_id: 331
wordpress_url: http://blog.andvari.it/2008/03/13/larte-di-arrangiarsi-circuiti-postscript-e-png/
tags: italiano
date: 2008-03-13 22:38:30.000000000 +01:00
---
Dico sempre che una delle qualità fondamentali è l'arte di arrangiarsi, e questa mia frase si applica perfettamente anche all'informatica.

Per la relazione di fisica sulle leggi di Ohm (resistenza e resistività) ho dovuto disegnare due circuiti, uno <a href="http://www.andvari.it/docs/blog_files/resistenze_serie.png">con le resistenze in serie</a>, l'altro <a href="http://www.andvari.it/docs/blog_files/resistenze_parallelo.png">con le resistenze in parallelo</a>.

Cosa ho fatto?

Ho provato a installare <a href="http://en.wikipedia.org/wiki/XCircuit">XCircuit</a> qua su Ubuntu Gutsy. Niente. Cioè, il programma funziona, però non come dovrebbe e non riesco a inserire gli oggetti come le resistenze, etc.

Ho aperto VirtualBox e avviato la mia copia virtuale di Winzozz Xp, scaricato la versione di XCircuit per quel OS (che poi OS non è, ma questa è un'altra storia) e alla fine ha funzionato.

Terminato di disegnare i due circuiti dopo una serie abbastanza lunga di bestemmie (quando ce vo' ce vo' ) mi sono ritrovato con il problema del formato in cui esportarli. Avevo letto <a href="http://en.wikipedia.org/wiki/Wikipedia:WikiProject_Electronics/How_to_draw_SVG_circuits_using_Xcircuit">una guida</a> che forniva un metodo abbastanza agevole per convertire i file PostScript in cui salva il programma in SVG, ma, poiché Murphy veglia su di me, non ha funzionato.

Provo <a href="http://www.karakas-online.de/myLinuxTips/ps2png.html">ps2png</a>, ma nisba anche questo. Cioè, funzionava ma praticamente mi forniva un png con solo la parte iniziale del circuito, ritagliata.

Come ho risolto? Aperto il file .ps con Evince (lo stesso che uso per gestire i .pdf ) e ho fatto un bello screenshot, ritagliato con GIMP.

Quando l'ignoranza e la sfiga abbondano, non resta altro che arrangiarsi.
