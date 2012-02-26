---
layout: post
title: Shortcuts in WinEDT 6
wordpress_id: 1821
wordpress_url: http://blog.andvari.it/?p=1821
tags: english
date: 2010-10-15 11:10:36.000000000 +02:00
---

Recently i swapped from WinEDT 5.5 to WinEDT 6, and i got really confused about the new interface. Everything i was familiar with, is now just gone.

I would not define myself a ninja-user of this program, but i know how to make myself more comfortable with it. For example, I am used, when writing in LaTeX, to have a couple of shortcuts: since I've been writing a Programming Book, I have to type a lot of <em>verbatim</em> and <em>verb </em>environments, so it comes handy to have a shortcut for that, and i chose to have Alt+&lt;.

In the previous version of  WinEDT, the shortcut customizations was not simple, but after 5 minutes of wandering on the menus, you will eventually figure it out how to start.

The secret is within the word <em><strong>Macro</strong>. </em>As i said, this program interface and the wide range of customization available can get everybody confused, so i just looked for something similar to what i needed, the bold shortcut, for example. And after a couple of clickety-clicks of the mouse, i copied the Bold.edt macro (which can be found in "C:\Program Files (x86)\WinEdt Team\WinEdt\Menus\Insert" and replaced what needed to be replaced to work with the new macro i was looking for. And then, it was just a matter of simple clicks.

With the major interface changes that came this March along with the new version of the program, the "Menu Setup"  dialog i was so comfortable with, is nowhere to be found.

I can see the reason behind this major changes, but everything got a LOT less newbie-friendly.  Now, everything, and i mean <strong>everything</strong> is stored under files. If you have to change the font, do not expect to go to "Options &gt; Preferences" and find a tab with "Font". These settings are now stored in this file: "C:\Program Files (x86)\WinEdt Team\WinEdt 6\ConfigEx\Font.ini". I will have to admit, all these files are easy to reach within the GUI of the program, but everything could be better explained.

Now (I'll try to stick with the topic of this post, this time) I'll explain how to define new shortcuts with WinEDT 6.

To begin with, everything you need is under MainMenu.ini (you will find it, eventually - it's the first choice in the new option menu - )
<ol>
	<li>Go to "C:\Program Files (x86)\WinEdt Team\WinEdt 6\Menus\Insert" (or something similar, you know how this works) copy and paste the bold.edt file, rename it freely and edit it with WinEDT.</li>
	<li>Customize the content of the file. In my case what i needed was</li>
<code>// Verb
IfisMode('TeX;BibTeX','%!m',!'InsLabel("\verb","|","|");Exit;');
InsLabel("\verb","|","|");]
End;
// Verb
IfisMode('TeX;BibTeX','%!m',!'InsLabel("\verb","|","|");Exit;');  InsLabel("\verb","|","|");]
End;</code>
	<li>Go to MainMenu.ini and look for "emphasize" (you can customize it to use the shortcut Ctrl+I later, if you want to)</li>
	<li>Copy the whole block of instructions that relate to emphasize and Paste it just below.</li>
	<li>Customize this block how you want it. For me was</li>
<code> ITEM="Verb"
CAPTION="&amp;Verb"
IMAGE="Teletype"
MACRO="Exe('%b\Menus\Insert\Verb.edt');"
REQ_DOCUMENT=1</code>
	<li>At the end of the macro line, press return and type<code> SHORTCUT=""</code>. You will notice that the top of options menu on the left has different icons, this time. Load Current Script / Insert Image / Insert shotcut / Insert item ... etc.</li>
	<li>Press the "Insert shorctut" button and define your shortcut. Press Ok and don't forget to add  " at the end of the line (i don't know why, but it seems to remove it all the time) For me the shortcut was:<code> SHORTCUT="32858::Alt+Z"</code></li>
	<li>Reload the script (right click on MainMenu and click on the proper item)</li>
	<li>Done. :)</li>
</ol>
Many many thanks to this guide: <a href="http://article.gmane.org/gmane.editors.winedt/5256/match=shortcut">http://article.gmane.org/gmane.editors.winedt/5256/match=shortcut</a>
