---
layout: post
title: Rendere StarCraft giocabile con Jaunty e Intel 945GM
wordpress_id: 1484
wordpress_url: http://blog.andvari.it/?p=1484
tags: italiano
date: 2009-05-26 12:30:54.000000000 +02:00
---
Ho <a href="http://blog.andvari.it/2009/05/01/e-la-lepre-cornuta-arrivo/">da poco</a> aggiornato Ubuntu alla 9.04 (Jaunty Jackalope), e, rapito dai video (tipo <a href="http://www.youtube.com/watch?v=9GpRCvLr79A">questo</a>)  di Starcraft 2 su YouTube e dai <em><a href="http://eu.starcraft2.com/features/battlereports/1.xml">Battle</a> <a href="http://eu.starcraft2.com/features/battlereports/2.xml">reports</a></em> ufficiali della <em>Blizzard</em>, mi è venuta voglia di rigiocare all'originale, uscito ormai oltre 11 anni fa (era infatti il lontano 1 aprile 1998).

Vabbé insomma, un po' di tempo fa (qualche mese) ci avevo giocato tranquillamente e mi ricordavo di non aver avuto nessun problema con Wine, andava tutto alla perfezione, non si vedeva la differenza con Winblows. E, giustamente, mi aspettavo che anche questa volta sarebbe andato tutto liscio, ma non avevo considerato la presenza del buon (caro) vecchio (amico) Murphy.

Per non farla troppo lunga, l'aggiornamento all'ultima versione di Ubuntu aveva peggiorato le qualità del mio video, tant'è che i fps erano decisamente bassi (misurati con <em>glxgears</em>). Erano così bassi che StarCraft era praticamente ingiocabile. Credevo fosse colpa di Wine, o chennesò. E mi sbagliavo.

È comunque colpa della mia scheda video, un'integrata Intel 945GM

È stata una lunga <em>quest</em>, ma alla fine ce l'ho fatta a sistemare. Tutta colpa di Intel, del Kernel nuovo e bla bla bla. Incollo qui le guide che ho usato:
<ul>
	<li><a href="http://pastebay.com/18054">http://pastebay.com/18054</a> (trovata su AppDB di WineHQ, nella sezione di StarCraft BroodWar 1.x, "Cure for slowness", incollata su Pastebay per comodità</li>
	<li><a href="https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4">Reverting the Jaunty Xorg intel driver to 2.4</a></li>
	<li><a href="http://ubuntuforums.org/showthread.php?t=449325&amp;highlight=starcraft2">HOWTO: Jaunty Intel Graphics Performance Guide</a> (usato la Safe, ero tentato dalla Optimal ma mi sono tenuto il Kernel 2.6.28)</li>
</ul>
Il primo link non so quanto sia stato utile, so che ora va bene, ma solo dopo che ho fatto il 2° e 3° passaggio (soprattutto il 3°, dato che il 2° mi aveva fatto guadagnare solo in framerate ma non con StarCraft).

In generale i miei fps sono passati da:
<ul>
	<li>Iniziali: ~140 fps</li>
	<li>Dopo essere ritornato al driver 2.4:  ~400 fps</li>
	<li>Dopo aver aggiornato i driver Xorg dal X-Uptags: italiano
dates PPA, Abilitato UXA, workaround per MTRR: ~800 fps</li>
</ul>
So solo che ora funziona a meraviglia, e posso mostrare la mia incapacità con un gioco del genere.
