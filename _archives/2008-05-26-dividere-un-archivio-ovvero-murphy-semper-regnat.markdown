---
layout: post
title: Dividere un archivio, ovvero "Murphy semper regnat"
wordpress_id: 445
wordpress_url: http://blog.andvari.it/?p=445
tags: italiano
date: 2008-05-26 20:46:52.000000000 +02:00
---
Supponiamo di avere un file .iso di 6,4 Gb da trasferire su un altro computer in LAN.
<ul>
	<li>Opzione 1: Trasferire l'iso via rete:
Scartata: 9 ore sono troppe</li>
</ul>
<ul>
	<li>Opzione 2: Scompattare l'iso e trasferirla a pezzi
Iniziata: Ma ci sono alcuni file più grandi del dispositivo che uso per il trasferimento (di 1 Gb)</li>
</ul>
Al che, per proseguire nell'opzione 2, bisogna pensare ad un modo per suddividere i file in dimensioni più piccole, tenendo conto che il file andrà scompattato su Windows (<em>sic</em>).

Il fido Valepert, sempre presente a dare una mano, ha linkato <a href="http://ubuntuhowtos.info/create_split_rar_archive">una guida</a>.  In sostanza basta dare questo comando:

<code>rar -m0 -v950M nomearchivio filedaarchiviare</code>

Ovviamente sono file di 1,9 e rotti Gb (che quindi NON stanno in 2 file 2, ma ben 3) e comincio a trasferire, una per volta, le 3 parti del file formato. Devo dire che è seccante dover maneggiare una chiavetta come se si trattasse dello strumento del mestiere di un attore porno, ma tant'è.

Poi, dopo che avevo già fatto un po' di fatica e separato tutti i file (erano 4, da 2 Gb ciascuno), mi ricordo di avere l'iPod da 30Gb con ancora quasi 20Gb di spazio vuoto. Potevo trasferire direttamente l'iso da lì, in 10 minuti al massimo. E io ci ho messo un bel po' di tempo. Mapporc.

(Però almeno con Kopete ho risolto, bastava un riavvio)
