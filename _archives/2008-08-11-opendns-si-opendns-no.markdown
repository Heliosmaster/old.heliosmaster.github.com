---
layout: post
title: OpenDNS sì, OpenDNS no?
wordpress_id: 883
wordpress_url: http://blog.andvari.it/?p=883
tags: italiano
date: 2008-08-11 10:38:07.000000000 +02:00
---
Ieri, per l'ormai noto casino legato a ThePirateBay avevo parlato di un possibile impiego di OpenDNS per aggirare in futuro i blocchi e le censure che potrebbero essere apportate appunto ai server DNS dei provider italiani.

Ovviamente (mi capita spesso) parlavo solo per sentito dire e non avevo mai direttamente provato suddetti DNS perché non ho mai avuto necessità / voglia di andare a paciugare nel mio router. Ieri, per il motivo suddetto, ho provato, e non ne sono rimasto affatto soddisfatto.

Innanzitutto, cos'è più precisamente openDNS? <a href="http://en.wikipedia.org/wiki/OpenDNS">Traduco</a> a spanne dalla Wikipedia in inglese (quella italiana ha un paio di righe e basta)
<blockquote>OpenDNS offre servizi di risoluzione dei DNS in alternativa a quella offerta dagli ISP. OpenDNS di solito processa le richieste più velocemente, aumentando in questo modo la velocità di reperimento di unas pagina.

Altre funzioni in aggiunta sono il filtro per il phishing e la correzione dei typo (scrivendo un indirizo .cmo anziché .com, l'url viene riscritto correttamente con il .com )</blockquote>
Questo è in sostanza ciò che offre. I problemi sono diversi:
<ol>
	<li>A discapito del nome, il software non è open source (Ok, ai fini tecnici non è molto rilevante, ma tant'è)</li>
	<li>Google e OpenDNS si odiano. Qualche esempio?</li>
</ol>
<!--more-->

Premetto subito che openDNS, a quanto ho capito, usa un sistema centralizzato per la gestione dei DNS: ovvero, non appena un utente digita un indirizzo di un dominio che vorrebbe visitare, la richiesta viene <strong><em>prima e comunque</em></strong> inviata ai server di openDNS e in seguito redirezionata sul sito. Ciò può causare notevoli ripercussioni. Ad esempio, se uno digita www.google.com non finirà nella stessa pagina che con i DNS del proprio provider, ma in una copia nei server di openDNS, la prova è questa query:
<blockquote>; &lt;&lt;&gt;&gt; DiG 9.3.2 &lt;&lt;&gt;&gt; @208.67.222.222 www.google.com

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         30      IN      CNAME   google.navigation.opendns.com.
google.navigation.opendns.com. 30 IN    A       208.69.34.230
google.navigation.opendns.com. 30 IN    A       208.69.34.231

---
2nd query using my ISPs DNS server:

;; QUESTION SECTION:
;www.google.com.                        IN      A

;; ANSWER SECTION:
www.google.com.         566561  IN      CNAME   www.l.google.com.
www.l.google.com.       58      IN      A       209.85.129.147
www.l.google.com.       58      IN      A       209.85.129.99
www.l.google.com.       58      IN      A       209.85.129.104

;; AUTHORITY SECTION:
l.google.com.           48162   IN      NS      e.l.google.com.
l.google.com.           48162   IN      NS      f.l.google.com.
l.google.com.           48162   IN      NS      g.l.google.com.
l.google.com.           48162   IN      NS      a.l.google.com.
l.google.com.           48162   IN      NS      b.l.google.com.
l.google.com.           48162   IN      NS      c.l.google.com.
l.google.com.           48162   IN      NS      d.l.google.com.

;; ADDITIONAL SECTION:
a.l.google.com.         48295   IN      A       209.85.139.9
b.l.google.com.         48295   IN      A       64.233.179.9
c.l.google.com.         48295   IN      A       64.233.161.9
d.l.google.com.         48295   IN      A       66.249.93.9
e.l.google.com.         48295   IN      A       209.85.137.9
f.l.google.com.         48295   IN      A       72.14.235.9
g.l.google.com.         48295   IN      A       64.233.167.9</blockquote>
La prima è fatta con openDNS, la seconda con i DNS di un altro ISP. Questo genera preoccupazione se si pensa che fra il motore di ricerca e adsense, almeno l'80% del traffico passa per qualcosa di Google. (Questo sarebbe già preoccupante di per sé, ma è un'altra storia) E sinceramente, non vorrei che OpenDNS ficcasse il naso in cose che non lo riguardano.

Il secondo grande problema che ho riscontrato è nella typo correction. Praticamente sovrascrive anche quella bellissima funzione della urlbar di firefox, (personalizzabile con la chiave <strong>keyword.url</strong> in <em>about:config</em>) che permette usare la funzione <em>i'm feeling lucky</em> semplicemente scrivendo una parola nella barra delle url di firefox. Potrà non essere una funzione chiave, ma diciamo che ha anche un effetto secondario, più nascosto. La maggior parte delle url ben scritte comprende il www, ma io, personalmente, e chissà quanti altri, non lo scrivo mai, perché penso che firefox lo metta da solo.

<strong>Errato</strong>. Firefox non glielo mette da solo, stiamo inconsciamente utilizzando la funzione dei fortunati espressa precedentemente. Ne ho avuto la prova ieri, quando, con openDNS, ho scritto nella mia barra degli indirizzi "nikon.it" e sono finito nella pagina che openDNS usa solitamente quando metti una sola parola, ovvero in una pagina targata openDNS che ti fornisce i risultati della tua ricerca, come se fosse un motore di ricerca. Il problema è che in quella pagina è presente della pubblicità che porta soldini in tasca a openDNS, mentre il secondo, più tastabile problema, è che il motore di ricerca usato è quello di yahoo, a mio avviso molto inferiore rispetto a Google.

Questa funzione sarebbe disabilitabile, ma vediamo che entra in gioco un altro difetto di openDNS: non prendere in considerazione gli ip dinamici.

Per com'è fatto, openDNS permette all'utente, una volta registrato, di poter personalizzare tutte le <em>ficciur</em> di quel servizio, a patto però di aggiungere un <em>network</em>, ovvero un ip (oppure una sottorete) sul quale queste regole saranno in vigore. In pratica tutte le volte che ci si scollega e ricollega a internet, dato che per la maggior parte delle persone cambia l'indirizzo IP, tali regole sarebbero da reimpostare. Per ovviare al problema ci sono diversi client che aggiornano automaticamente il <em>network</em>, ma questo a mio avviso non risolve il problema. Tanto che un'utente che utilizza openDNS e che casualmente ha l'ip che avevo io ieri, si ritroverà le regole che avevo impostato io.

A tutte le critiche sopra esposte, openDNS ha risposto con frasi del tipo "Google is not an option." o cose del genere, rimanendo sempre sul vago.

Che sia questo il prezzo della libertà? Non lo credo. E per ora mi tengo i DNS di Libero.
