---
layout: post
title: Ritornare da Amarok 2.x a Amarok 1.4
wordpress_id: 1460
wordpress_url: http://blog.andvari.it/?p=1460
tags: italiano
date: 2009-05-02 15:24:52.000000000 +02:00
---
Questo è un post per tutti quelli delusi da Amarok 2.x. Sì ok, è bello e tutto quanto, ma ci sono la metà delle funzioni (più o meno).

A mio avviso Amarok 1.4 andava così bene! :) Ed ecco il modo per ritornare alla vecchia versione (testato con Ubuntu Jaunty):

<strong>Sistema &gt; Amministrazione &gt; Sorgenti software</strong>

Nella scheda "Software di terze parti" cliccare su "aggiungi" ed incollare la seguente riga:
<pre> deb <a href="http://ppa.launchpad.net/bogdanb/ppa/ubuntu">http://ppa.launchpad.net/bogdanb/ppa/ubuntu</a> <span id="series-deb">jaunty</span> main</pre>
In seguito cliccare sulla sua chiave pubblica, ovvero <a href="http://keyserver.ubuntu.com:11371/pks/lookup?op=get&amp;search=0xB9F1C432AE74AE63">qua</a>, poi "Mostra l'originale" (se usate Gnome, altrimenti credo che questo passo non serva), copiare e incollare quel codice in un qualunque editor di testo e salvarlo con un qualunque nome.

Ritornare alla finestra di prima (quella Sorgenti Software) e alla scheda "Autenticazione" cliccare su Importa e selezionare il file salvato prima.

Ora chiudere la finestra e cliccare su "ricarica" quando si viene avvisati che la lista dei pacchetti non è aggiornata.

Poi aprire il terminale e digitare:
<pre>sudo apt-get remove amarok &amp;&amp; sudo apt-get install amarok14</pre>
<em>et voilà</em>
