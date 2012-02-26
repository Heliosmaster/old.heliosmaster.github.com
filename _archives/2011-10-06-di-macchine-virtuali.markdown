---
layout: post
title: Di macchine virtuali
wordpress_id: 1983
wordpress_url: http://blog.andvari.it/?p=1983
tags: italiano
date: 2011-10-06 00:38:04.000000000 +02:00
---
Sì, lo so, sono in debito di almeno un post sulla mia avventura olandese: spero di trovare presto il tempo necessario.

Quello di cui vorrei parlare stasera è un po' un resoconto/promemoria di una delle tante peripezie che succedono a <em>paciugare</em> con robe un po' particolari: le macchine virtuali.

Per vari motivi, di cui non parlerò, io uso Windows 7 e per praticamente tutte le cose che devo fare di "lavoro" (sia per piacere che per l'università) uso una macchina virtuale con su Ubuntu installato. E va tutto a meraviglia (presto ci faccio girare anche le cose in parallelo fra una macchina e l'altra, a momenti). O meglio, andava.

Oggi, sul tardo pomeriggio, mi sono apprestato ad aggiornare la versione di VirtualBox alla 4.1.4, e sono cominciati i miei guai: ha cominciato a lamentarsi che il modulo del kernel non era stato adeguatamente installato, o una cazzabubbola del genere. Mah.

Provo a reinstallare, niente.

Provo a fare un revert alla versione 4.1.2, ma niente.

Paciugo per mezz'ora provando a togliere e rimettere le macchine virtuali (tenendomi ben stretto il file <em>buntu.vdi</em> che contiene l'hard disk virtuale, con tutti i dati (no, non temete, nonostanti usassi Ubuntu, le mie directory di lavoro essenziali erano su Dropbox (tramite una cartella condivisa) e comunque le cose importanti / di programmazione sono anche in una copia su GitHub.

<strong>Fermi tutti, chiamate la neuro</strong>: ho appena riletto l'ultima frase e mi chiedo come ho fatto a pensare che un periodo tale potesse risultare comprensibile. <em>Long story short</em>: è un po' un casino ma nel caso peggiore, ovvero che dovessi buttare tutto e ripartire da zero con la macchina virtuale, non avrei perso nulla perché tutte le cose importanti sono salvate, in vari posti.

Vabbé insomma, "VirtualBox <em>non s'ha da fare</em>" (cit.)

Qualche tempo fa, un po' così per gi<em>u</em>oco, ho provato a *ehm* installare OSX Lion virtualizzato *ehm*, e per fare ciò è servita una copia, prestata da *ehm* un amico *ehm*, di VMWare Workstation.

Beh, allora mi son detto: "Già che <em>c'hai</em> un altro programma di virtualizzazione nel tuo sistema, perché non provare a fare in modo di vedere il vecchio Ubuntu tramite quello?".

Beh, sì, teoricamente suona bello. Peccato che i formati non siano minimamente compatibili. Però, fortunatamente, internet mi ha aiutato.
<ol>
	<li>Convertire l'immagine VirtualBox (.vdi) in formato raw (.raw) usando un tool stesso (da riga di comando di Windows, che orrore!) di VirtualBox.</li>
	<li>Convertire l'immagine raw in formato VMWare (.vmdk) usando Qemu</li>
	<li>Creare una nuova macchina virtuale su VMWare (in modo che crei lui i file di configurazione)</li>
	<li>Rimpiazzare brutalmente il file .vmdk in modo da usare l'hard disk che già avevamo.</li>
</ol>
Una guida fantastica che ho trovato, è stata <a href="http://www.sysprobs.com/convert-vdi-vmdk-open-sun-virtualbox-virtual-machine-vmware-player-workstation">questa</a>. E funziona esattamente come dovrebbe.

Tuttavia, non finiscono qua i problemi della serata! Ovviamente la macchina virtuale era configurata per girare <em>seamlessly</em> sotto VirtualBox, ma VMWare è tutta un'altra storia. Urge installare degli appositi <em>tools</em>, peccato che nel frattempo è finito lo spazio.

E allora? Beh, dobbiamo ingrandire l'hard disk virtuale, peccato che non sia così semplice.
<ol>
	<li>Ingrandire l'hard disk usando un tool (ancora da riga di comando di Windows, orrore!/2) specifico di VMWare</li>
	<li>Visto che non è possibile estendere la partizione mentre la si usa, creare una macchina virtuale nuova</li>
	<li>Usare nella seconda macchina virtuale il LiveCD di Ubuntu</li>
	<li>Usare Gparted e ingrandire la partizione.</li>
</ol>
Ancora un grazie,<a href="http://expectus.hubpages.com/hub/How-to-Increase-VMware-Hard-Disk-Space"> a questa guida</a>.

Ok, ora c'è sufficiente spazio nell'hard disk per installare i tools, procediamo!

Ehi, va tutto bene.. tranne che a un certo punto qualcosa va storto e alcune funzionalità non vengono installate (tra l'altro, è davvero molto user-friendly la loro installazione, spiegano passo passo quello che succede in maniera giusta, gentile e precisa).

E allora? Beh, <a href="http://gordonazmo.wordpress.com/2011/02/09/fixing-vmware-tools-vmhgfs-on-newer-kernels-probably-anything-2-6-36/">facile</a>,vai in <code>/usr/lib/vmware-tools/modules/source</code> e spacchetta il file <code>vmhgfs.tar</code>, modifica il file <code>super.c</code>, rimpacchetta tutto e fai ripartire la configurazione.

Sì, è un casino, ma poi almeno la funzionalità delle shared folder è stata installata.

Chiudo qua, con lo stato delle cose in questo modo. Un solo commento: avevo evidentemente un bel po' di karma da recuperare, ma mi son divertito.
Ps. mi sembra di esser tornato un nerd sedicenne, usando questo tono così intenibile. Scusatemi.
