---
layout: post
title: Personalizzare il menu in Gnome
wordpress_id: 464
wordpress_url: http://blog.andvari.it/?p=464
tags: italiano
date: 2008-06-19 19:26:18.000000000 +02:00
---
Ecco un paio di semplici passaggi per personalizzare il menu in Gnome e creare dei collegamenti, più o meno elaborati, alle altre applicazioni.
<ol>
	<li>Cliccare con il pulsante destro su "Applicazioni" e poi "Modifica menù" (facile, no?)</li>
	<li>Per creare un "launcher" di un programma che sia un po' più complesso (intendo, non l'esecuzione di un binario in /usr/bin o <em>similia</em>) dobbiamo appoggiarci alla mitica shell. Se, ad esempio, dobbiamo spostarci in una determinata cartella per lanciare il comando "Wine XXX.exe" (sarebbe meglio di no, visto che a noi le cose Winzozz ripugnano, ma non si sa mai :P ), nel comando del launcher inserire questa semplice stringa</li>
</ol>
<code>sh -c "cd /home/percorso/della/cartella &amp;&amp; wine XXX.exe"</code>

Può essere ovvio, come può non esserlo (io per esempio non sapevo di "sh -c" per eseguire comandi in linea :P )
