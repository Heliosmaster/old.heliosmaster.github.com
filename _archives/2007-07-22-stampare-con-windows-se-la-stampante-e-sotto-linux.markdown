---
layout: post
title: Stampare con Windows se la stampante è sotto Linux
wordpress_id: 185
wordpress_url: http://blog.andvari.it/2007/07/22/stampare-con-windows-se-la-stampante-e-sotto-linux/
tags: italiano
date: 2007-07-22 11:02:33.000000000 +02:00
---
Ebbene oggi ho dovuto un po' darmi da fare, ma alla fine ce l'ho fatta, e ne sono orgogliosissimo:

Ringrazio <a href="http://www.openlinux.eu/content/view/29/39/">questa guida</a>, senza di essa non ce l'avrei mai fatta, e rimando chiunque voglia fare ciò a seguire il procedimento ivi descritto, che riporto qua sotto in breve:

Operazioni da fare nel pc Linux
<ol>
	<li>Verificare che la stampante sia collegata al PC Linux e usi i drivers CUPS</li>
	<li>Andare su <a href="http://localhost:631">http://localhost:631</a></li>
	<li>Cliccare sulla scheda "Amministrazione" e spuntare le caselle <span style="font-style: italic">"Condividi le stampanti pubblicate connesse a questo sistema"</span><br style="font-style: italic" /><span style="font-style: italic">"Consenti amministrazione remota"</span></li>
	<li><span style="font-style: italic"></span>$ /etc/init.d/cupsys restart</li>
	<li>Annotarsi l'ip locale della macchina (nel mio caso 192.168.1.3, ottenuto tramite il pannello di amministrazione del router, ma un ifconfig basta e avanza)</li>
	<li>e in <a href="http://localhost:631/printers/">http://localhost:631/printers/</a> annotarsi la descrizione della stampante, nel mio caso "Stylus-Photo-R300"</li>
</ol>
Operazioni da fare nel pc Winzozz (mi dispiace per voi che l'usate :P ), preferibilmente XP (Vista fa ancora più cagare, ardua impresa :P )
<ol>
	<li>Pannello di controllo -&gt; Stampanti e Fax -&gt; Aggiungi Stampante</li>
	<li>Scegliere "Stampanti di rete o stampanti collegate ad un altro computer"</li>
	<li>Cliccare su "Connetti ad una stampante in Internet o della rete domestica o aziendale"</li>
	<li>Inserire "http://IP:631/printers/DESCRIZIONESTAMPANTE" nel mio caso "http://192.168.1.3:631/printers/Stylus-Photo-R300"</li>
</ol>
Et voilà, la <del>magia</del> potenza dell'informatica, e di <strong>Linux</strong>.
