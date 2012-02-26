---
layout: post
title: L'odissea di Wordpress
wordpress_id: 6
wordpress_url: http://blog.andvari.it/2007/10/02/lodissea-di-wordpress/
tags: italiano
date: 2007-10-02 21:36:13.000000000 +02:00
---
Importare i post da un precedente database di Wordpress è un casino.

Ecco gli errori a caso:
<ul>
	<li>La versione 2.0.3 non supporta l'esportazione nel formato WXR che il nuovo Wordpress 2.3 mastica benissimo, ergo montare il vecchio database in una nuova installazione di WP 2.3 ed esportarli</li>
	<li>Errori nella codifica delle lettere accentate, molti errori.</li>
	<li>Vengono importati solo 2-3 post per volta, e ogni volta che tenti di importarli crea altrettante utenze del blog vuote assegnandole come "sottoscrittori" ed autori di massimo 1 post</li>
	<li>VV.EE.</li>
</ul>
Sono diverse ore che mi sono messo e non ci sono riuscito, ciò che ne ho ricavato è:
<ul>
	<li> ho dovuto ricreare completamente il database salvando solo la tabella wp_options (per fortuna)</li>
	<li>ho imparato un po' di comandi mysql</li>
</ul>
Uno dei passaggi intermedi è stato:

mysql&gt; CREATE TABLE wp_comments (
comment_ID bigint(20) unsigned NOT NULL auto_increment,
comment_post_ID int(11) NOT NULL default '0',
comment_author tinytext NOT NULL,
comment_author_email varchar(100) NOT NULL default '',
comment_author_url varchar(200) NOT NULL default '',
comment_author_IP varchar(100) NOT NULL default '',
comment_tags: italiano
date tags: italiano
datetime NOT NULL default '0000-00-00 00:00:00',
comment_tags: italiano
date_gmt tags: italiano
datetime NOT NULL default '0000-00-00 00:00:00',
comment_content text NOT NULL,
comment_karma int(11) NOT NULL default '0',
comment_approved enum('0','1','spam') NOT NULL default '1',
comment_agent varchar(255) NOT NULL default '',
comment_type varchar(20) NOT NULL default '',
comment_parent bigint(20) NOT NULL default '0',
user_id bigint(20) NOT NULL default '0',
PRIMARY KEY  (comment_ID),
KEY comment_approved (comment_approved),
KEY comment_post_ID (comment_post_ID)
);

Che pacco.

<strong> Aggiornamento:</strong>

Sono riuscito a ripristinare tutto, era la tabella wp_options che faceva casini, quindi ho solo dovuto riconfigurare tutto il blog. Pazienza.
