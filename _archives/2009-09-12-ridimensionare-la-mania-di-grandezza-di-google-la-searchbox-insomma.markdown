---
layout: post
title: Ridimensionare la mania di grandezza di Google (la searchbox, insomma)
wordpress_id: 1589
wordpress_url: http://blog.andvari.it/?p=1589
tags: italiano
date: 2009-09-12 12:11:51.000000000 +02:00
---
Recentemente, cioè tipo 3 giorni fa, Google ha fatto una modifica: allargare la propria barra.

C'è chi se n'è accorto, c'è chi non se n'è accorto, ma vabbé.

Io penso che Google abbia fatto una cazzata, se non altro perché non ha dato possibilità agli utenti di decidere se la volevano meglio prima (un bel "switch to old version" non avrebbe fatto male). Io sono un utente molto abitudinario, per queste cose. Se mi vai a cambiare anche solo il font io mi sento così a disagio, che mi sembra di indossare la maglia di qualcun altro.

E così, pochissime ore dopo il rilascio, quando i principali siti di notizie informavano del cambiamento, ho iniziato a cercare per il web di una possibile patch, cioè di uno script greasemonkey che potesse fare al caso mio.

E <a href="http://userscripts.org/scripts/show/57449">l'ho trovato</a>.

Però poi c'è da fare una piccola modifica, perché questo script qua non modifica l'altezza delle linee nei suggerimenti, e quindi bisogna aggiungere:
<code>GM_addStyle(
'.gac_m td {' +
' line-height:16px;}'
);</code>

in un punto qualunque.

L'ho proposto anche all'admin di quello script, sperando che lo includa il più presto possibile.

PS. grazie a Pietrodn che mi ha aiutato a capire come fixare la roba della line-height.
