---
layout: post
title: "Creating launchers for gnome 3 shell"
tags: english
---

I recently switched to [Sublime Text 2](http://www.sublimetext.com/2). Believe me, it's amazing. And in this small post I will explain how to create a launcher for it (or basically any other applications installed) in the "sidebar" of Gnome3.

This is because I use Linux Mint 12 Lisa, which is basically Ubuntu without Unity and with Gnome3 + Mate (I have never been happier with a DE); in this framework there are no problem with adding to the "favorites" of the Gnome 3 shell any program that was installed via apt-get or any .deb package, as usual.

ST2, instead, did not come with a .deb package, but just the binaries inside a simple archive; so, no default way to put such program to my favorites, apart from creating a desktop icon (and, as I realized lately, desktop icons are not useful anymore with the new generation of DEs, such as Gnome3, Unity, OSX's docks, and are used really only under Windows), which was not really what I wanted.

The solution of this problem was not particularly hard, but I believe that with this post some people could save some search time (and of course, I won't need to search it again!).

Let us suppose (pardon my mathematical language, I deal with it every day) that we have uncompressed our ST2 archive in the folder `~/comp/Sublime Text 2` (I reccomend putting all the software installed _by hand_ in a separate folder, so it can be easy found: the "comp" is actually for "compiled", even thought there's nothing to compile for ST2).

1. Being a guy which uses a lot the terminal (and you should do that as well!) I naturally want to start being sure that there is a shortcut. `st` seemed a reasonable choice (when trying to type that in the terminal, Linux told me that it was related with the `suckless-tools` package, which I probably won't need to install ever): therefore

	`sudo ln -s ~/comp/Sublime Text 2/sublime_text /usr/bin/st`

	provided that `/usr/bin` is in your PATH (which will already be, probably)

2. We need to create the launcher itself, which is done by creating a `st.desktop` file in `~/.local/share/applications` with this content:

	<pre>[Desktop Entry]
	Type=Application
	Exec=st
	Name=Sublime Text 2
	Icon=~/comp/Sublime Text 2/Icon/128x128/sublime_text.png</pre>

3. Just search for Sublime Text in the Gnome 3 Shell and pin it to "favorites".
4. Profit (not really).



