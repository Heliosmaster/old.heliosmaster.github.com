---
layout: post
title: Comprimere i video con Avidemux per YouTube
wordpress_id: 156
wordpress_url: http://blog.andvari.it/2007/12/29/comprimere-i-video-con-avidemux-per-youtube/
tags: italiano
date: 2007-12-29 12:10:38.000000000 +01:00
---
Visto che mi dimentico abbastanza in fretta, scrivo qua come si fa a comprimere un video per farlo stare nel limite dei 100 MB di YouTube, e, visto che magari altre persone potrebbero essere interessate, quale miglior luogo del blog?

Innanzitutto procurarsi <a href="http://fixounet.free.fr/avidemux/">avidemux.</a> Aprire il video da ridimensionare.

Nella parte sinistra dello schermo, di fianco all'anteprima del video, nel menu "Video" anziché copy mettere "Mpeg4 (lavc)", cliccare su configure: nella main tab, settare "Encoding type" in "two pass" , in "Target Size" mettere la dimensione voluta, "quantizer" lasciare così com'è.  Nel menu "Audio" anziché copy mettere "lame" (almeno io faccio così) e cliccando su configure settare il bitrate audio.

NB: Quando si imposta la dimensione voluta nel menu video, impostare sempre qualche mb in meno perché anche l'audio di solito tiene un po' di spazio, che non viene incluso nel conteggio di quel menu lì.

Salvare il video con "File" &gt; "Save" &gt; "Save Video".

Caricare su iutub.
