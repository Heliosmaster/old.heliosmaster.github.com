---
layout: post
title: Batch eps to pdf
wordpress_id: 1944
wordpress_url: http://blog.andvari.it/?p=1944
tags: italiano
date: 2011-07-07 11:48:11.000000000 +02:00
---
Lo so che non posto da una vita, ma non è ancora giunto il momento giusto perché mi esprima. Questo è un post di servizio, un <em>placeholder</em> per un comando che mi è tornato utile e che spero sia utile ad altri.

Da MATLAB usando il comando

<code>print -depsc -r300 filename</code>

si salva un immagine in formato .eps .

Se anche voi, come me, usate PDFLatex anziché Latex e basta, è necessario convertire i documenti in PDF.

Avessi avuto l'installazione di LaTeX sono Linux, non ci sarebbero stati problemi. Ma dato che è sotto windows, la cosa è un po' più complicata.

In aiuto ci viene il file <code>epstopdf.exe</code> , incluso automaticamente nell'installazione di MikTeX. Quando però sono tanti i file  .eps, come fare a non perdere un sacco di tempo?

<code>forfiles /m *.eps /c "cmd /c epstopdf @fname.eps"</code>

Et voilà.
