---
layout: post
title: "Vidalia and the Unity system tray"
tags: english 
---

I am definitely going to talk soon about [Tor](http://torproject.org), somewhat profusely. For now, be satisfied of this mini HOWTO.

I quite recommend the usage of [Tor Browser Bundle](https://www.torproject.org/projects/torbrowser.html.en), (if you don't know what is it, go immediately and take a look at its awesomeness!), but I discovered that a very small tweak is necessary in order to have the best possible experience when using Ubuntu with Unity.

In particular, I discovered that when I ran from the terminal

`./start-tor-browser`

(I am not using repositories, just the plain .tar.gz downloaded from the Tor website), the vidalia window correctly opened (also in the sidebar), but if I accidentally closed it, there was no way to get it back, that I know of. The problem was (is, actually) caused by the Unity policy of forbidding icons in the system tray, unless they are _whitelisted_.

So, in order to get our beautiful Vidalia icon, we have to proceed to whitelisting it.

* For the hardcore people that love the terminal (of course, props to you!) it is quite simple, and I recommend following [this nice guide on askubuntu](http://askubuntu.com/questions/35076/how-do-i-whitelist-truecrypt-to-show-in-the-indicator-area), although that it was conceived for _truecrypt_ it is still valid: instead of `truecrypt` just put `vidalia`. As a side note: if are not yet using truecrypt and Full Disk Encryption, take into consideration of making it one of your New Year Resolutions (cf. the last year [New Year's Resolution: Full Disk Encryption on Every Computer You Own](https://www.eff.org/deeplinks/2011/12/newyears-resolution-full-disk-encryption-every-computer-you-own)!
* Otherwise just open `dconf-editor` (either by launching it from terminal, or by looking for it in the Unity Dash) and look for **desktop.unity.panel**, as shown in the image below

 <img style="margin-left:auto;margin-right:auto;display:block;" src="http://i.imgur.com/wFJNUl.jpg" />

edit the value and append `vidalia`, as shown in the image.

_Et voilà_, now when you start the Tor Browser Bundle from the terminal, you will notice the desired onion icon in your Unity system tray.

And enjoy your anonimity, while you still can.
