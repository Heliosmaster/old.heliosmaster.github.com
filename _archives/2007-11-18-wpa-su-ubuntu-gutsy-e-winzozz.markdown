---
layout: post
title: WPA su Ubuntu Gutsy (e Winzozz)
wordpress_id: 92
wordpress_url: http://blog.andvari.it/2007/11/18/wpa-su-ubuntu-gutsy-e-winzozz/
tags: italiano
date: 2007-11-18 19:26:06.000000000 +01:00
---
Tutte le volte che faccio una miglioria o semplicemente "paciugo" con qualcosa di tecnico mi sento in dovere di scriverlo qua, sia per ricordarmi, che per renderne partecipi i pochi miei lettori, e infine perché le informazioni sono il concentrato di una ricerca su google che ha richiesto diversi minuti. Insomma, postando il risultato, farei felici tante persone, nonché il mio ego.

L'argomento di oggi è la crittazione della propria WLAN. Ammetto che per circa due anni la mia connessione è stata non protetta, ma non è stato un grosso problema fino ad ora perché il segnale fa molta molta fatica ad uscire dalla mia proprietà, quindi diciamo che ero abbastanza sicuro. Però, mi sono voluto cautelare e allora ho provato a proteggermi meglio:

Poiché la totalità del networking in casa mia si basa sul wireless, prima di cominciare mi sono procurato un bel cavo ethernet e ho attaccato il PC con dentro Vista (sic, non è mio), giusto per avere le "chiappe" protette nel caso qualcosa andasse storto e ripristinare tutto come prima.

Ho attivato la WEP a 128 bit:

Windows XP: Ok
Ubuntu: Network-manager mi chiede spontaneamente la password (solo dopo un riavvio però, altrimenti cerca ancora di connettersi senza nessuna chiave), a causa di una mia incomprensione, anziché mettere la parola chiave continuo a inserire le 26 cifre esadecimali, non appena mi accorgo dell'errore tutto funziona alla perfezione.

Però, poiché leggo che la WEP è molto meno sicura della WPA, decido di passare a quest'ultima:

Windows XP: Ok
Ubuntu: Con network-manager sembra che si stia connettendo, ma in realtà non chiede né password, né niente. Risultato è che non riesco a riconnettermi.

Riprovo a mettere WEP 128-bit:

Ubuntu: Ok subito (senza bisogno di rimettere la password, poi ho capito il perché*)
Windows: Non appena cercavo di connettermi cliccando due volte sulla connessione, rimaneva in attesa all'infinito.

Sconsolato, levo la protezione del tutto.

Dopo qualche minuto, fiducioso delle mie possibilità, e soprattutto perché ho trovato <a href="http://reubuntu.blogspot.com/2007/10/gestione-delle-reti.html">questa guida</a> , che ritengo perfettamente chiara e utile, ho riattivato la WPA.

Risultato, tutto funziona. Con mia estrema soddisfazione :)
E ora sento il sedere ancora più al caldo, quando vado su internet, peccato che network-manager non supporti ancora bene WPA, ma finché tutto funziona, non vedo perché lamentarsi.
