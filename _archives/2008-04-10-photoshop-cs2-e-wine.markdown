---
layout: post
title: Photoshop CS2 e Wine
wordpress_id: 367
wordpress_url: http://blog.andvari.it/?p=367
tags: italiano
date: 2008-04-10 21:36:04.000000000 +02:00
---
Se l'attivazione di Photoshop CS2 con Wine dà casini, del tipo: "spazio insufficiente nel disco" o qualcosa del genere (in inglese "not enough disk space" o <em>similia</em>), ecco un comodo sistemino per risolvere (prelevato da <a href="http://bugs.winehq.org/show_bug.cgi?id=10018#c16">questa pagina</a>)
<ul>
	<li>ls -l /dev/sda (annotarsi i permessi)</li>
	<li>sudo chmod a+rw /dev/sda (o hda, a seconda del tipo di HD che usate)</li>
	<li>Aprite Photoshop CS2 e provate ad attivare normalmente</li>
</ul>
Ora, per ripristinare i permessi com'erano:

Se, come me era <strong>brw-rw----</strong>
<ul>
	<li>sudo chmod o-rw /dev/sda</li>
</ul>
E tornerà tutto come prima
