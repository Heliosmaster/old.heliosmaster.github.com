---
layout: post
title: Sistemare i programmi predefiniti in Linux Mint/Ubuntu
wordpress_id: 2013
wordpress_url: http://blog.andvari.it/?p=2013
tags: italiano
tags: italiano
date: 2012-01-24 15:29:10.000000000 +01:00
---
Dato che come (La)TeX editor uso il fantastico Kile, ma sono sotto Gnome (3 shell, grazie a Linux Mint 12 Lisa, e sono anche contento!), fare il doppio click su un file .tex produce l'apertura del file stesso tramite <em>gedit. </em>E cliccare tutte le volte con il destro, "Open With", eccetera eccetera, beh, si fa, ma non è proprio il massimo.

Per fortuna ho trovato questa guida: <a href="http://ubuntuforums.org/archive/index.php/t-299086.html">http://ubuntuforums.org/archive/index.php/t-299086.html</a>

Tendenzialmente, ciao le cose da fare sono due:

`touch ~/.local/share/applications/defaults.list` (se non esiste)

`gedit ~/.local/share/applications/defaults.list` (o con qualunque altro programma di vostra scelta).

Ora, basta che all'inizio del file ci sia la stringa (precisa a questa, eh)

<code>[Default Applications]</code>

e sotto potete specificare i vostri programmi predefiniti, così:

<code>application/x-tex=kde4/kile.desktop</code>

et voilà, presto fatto.

Tra l'altro, con gnome, non c'è neanche bisogno di riavviare un fico secco. Doppio click, e via che si va.
