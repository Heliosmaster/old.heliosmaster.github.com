---
layout: post
title: Storie di webcam e di kernel
wordpress_id: 1593
wordpress_url: http://blog.andvari.it/?p=1593
tags: italiano
date: 2009-09-15 14:51:07.000000000 +02:00
---
C'era una volta..
No dai, non è una di queste storie.

Dato che non ci si può vedere fisicamente, si cerca di fare quel che si può con una miserrima webcam. Quando sono qua a casa dispongo di una abbastanza vetusta Logitech QuickCam Zoom, che a occhio e croce deve avere la risoluzione dell'occhio di una talpa, ma è meglio di niente. E, come dicevo, qua a casa la uso attaccata a un PC con dentro Winblows vista, gentilmente prestatomi da un mio altrettanto vetusto genitore.

Il fatto è che a Ferrara non mi è dato di portarmi dietro suddetto PC schifoso (solo perché ha un sistema operativo di cacca, e scusatemi se è poco) e, a quanto sapevo, la webcam QuickCam Zoom non è compatibile con il mio fantastico Ubuntu.

E allora, dopo una rapida Googlata, arrivo a <a href="http://bert.vdbstudios.be/ubuntu/webcam.php">questa</a> guida, con un link a <a href="http://www.lavrsen.dk/twiki/bin/view/PWC/InstallationStandAloneModuleKernel2x6">quest'altra</a> guida.

Ohibò, di scaricare un modulo sono anche capace, ma qua parla di ricompilare il kernel. Ok, qualcosina saprò fare con Linux, ma non mi sono dato a cose così. Meno male che nella seconda guida c'è qualcosa di più comprensibile. Fino a quando non leggo che bisogna patchare.

Non ho nemmeno capito *cosa* bisogna patchare, se il modulo o il kernel o miasorella.

Bene! Partiamo con il piede giusto!

Fortunatamente googlo ancora un pochettino e trovo un tizio che ha il mio stesso problema, nel senso che non solo deve far funzionare quella cam ma non ha idea di cosa debba fare, nel senso di comandi da dare in pasto alla super-duper commandline.
E leggo di un tizio che dice: non siamo più negli anni '90 (ne parla come se fossero vent'anni fa..ah ma è vero, sono quasi 20 anni fa :P ), se guardi molto probabilmente è già tutto fatto e incluso nella tua copia del kernel.

E in effetti, collegando la webcam via USB e dando comandi come lsusb, lsmod, modprobe pwc e locate pwc.ko, mi accorgo che effettivamente c'è già tutto quello di cui ho bisogno.

Allora apro Kopete e vedo che effettivamente la webcam funziona, e che forse mi ero sognato che non funzionasse.

Beh, meglio così.

Però ecco, mi accorgo che non so bene come fare a far funzionare la webcam e MSN con Kopete.. allora installo aMSN da repository, <em>et voilà.</em>

Bene, tutto soddisfatto mi accingo a fare una prova e, non appena aMSN mi chiede di procedere per la configurazione audio-video. Ok, mi dico, andiamo avanti.

E compare la prima schermata in cui bisogna scegliere quale webcam usare. Beh, vedo che l'immagine è chiara e nitida, molto migliore di quella che avevo con la webcam nel PC con windows. Ehi, ma aspetta un secondo, la webcam è appoggiata sul tavolo! Ma..l'immagine mi riprende dall'alto :S che succede?

E mi accorgo che effettivamente aMSN usava la webcam di cui il mio computer portatile è dotata, che in tutti gli altri programmi (Skype, Camorama) faceva più che cagare, invece con aMSN si vede così bene che quasi inorridisco. (per quello che vedo, cioè me :P )

Beh insomma questa piccola storiella serve a insegnare come a volte la soluzione sia davvero dietro l'angolo.
