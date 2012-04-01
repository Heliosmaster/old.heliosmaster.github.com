---
layout: post
title: "Manage a website with git and mirror it on GitHub"
tags: 
---

## DreamHost and the issue with cloning

Since the updating of the website [Bifröst.it](http://bifrost.it) is done via multiple locations, and it involves a **lot** of HTML files, we decided, a while back, to use git for its "development".

This was not particularly hard, following [this guide](http://toroid.org/ams/git-website-howto), and we managed to get everything up and running very quickly.

Things went fairly smoothly until our repository reached a *critical* size, or at least critical from the point of view of our hosting provider, DreamHost. In particular, the problem arose when some errors were made and there was mismatch with the local git repositories.

Since we are not particularly experienced with git (and we did not use GitHub and its comfy feature of viewing from a website the whole repository) we thought that it was better (and quicker) to simply *start again*, that is start a new repository, put the "good version" inside it, and just clone everything again on the various machines we used.

But we did not take into account the size of the repository, unluckily. The problem was that, in the process of cloning, git on the DreamHost server used too much (~500 Mb) memory and it was killed by the "guardian process" (I don't really know if that is the right terminology, but it is easily understandable what I mean). So, we could not clone anymore.

After trying all sorts of tricks with Git on Dreamhost (I recollect something with no_mmap, but surely I tried much more) and contacting directly DreamHost (after a **long** discussion, they simply concluded "anyway we don't officially support git so just use subversion", which made them lose a lot of points in my opinion) with scarce results, we tried to reduce the size of the repository: after all, not all the files were required (some of them will be used in the future, I guess, and they were simply there as placeholders), so we were able to cut a 30% of the total size. But still, no luck with DreamHost.

So we asked ourselves a bunch of questions:

* _Shall we stop using git and favore some other similar program?_ 
	
	No, because we slowly (not everybody participating is skilled with a computer) got used to it, and found it was a perfect match to our needs.

* _Shall we stop using DreamHost?_ 

	This question, in reality was more "Can we find an alternative host with the same budget that does not have these problems with git?" (the website is done completely out of passion, we never saw a cent of it.) So, this was not really easy to answer, and furthermore we just paid for another year at DreamHost.

So, no other alternative seemed particularly attractive, until (a couple of days ago) I realized that one of the most celebrated features of git, the fact that is decentralized, could really be helpful, in our case.

Another important piece of the puzzle (which is about to be solved) is that, when we switched to git, we did not think about using GitHub because we did not want all the files to be publicly browsable, and the idea to pay extra for "private repositories" was not particularly appealing (did I mention that we do not gain anything from this project, apart from pride?). 

This matter changed some months ago, when GitHub gifted me with two years of paid account because I am still a student, so now we could ask GitHub for help, which is exactly how we solved the problem.

The following steps, are basically a guide to set up a website on Dreamhost, versioned with Git, if the size is quite an issue:

1. From my local computer, I followed all the steps in [the original guide](http://toroid.org/ams/git-website-howto) we previously used.
2. I created a private repository on GitHub, added it as another remote from my local repo and pushed everything to it
3. From all other machines, we clone from GitHub and then set the remote to the DreamHost server.

And now everything works.

## Keeping the github repo up-to-date

The GH repo proved himself really handy, so it comes quite naturally that we want it to stick around: furthermore, as I already mentioned, the possibility to browse the code (althought HTML) and check out the diff in a neat way (sorry, I prefer it much more to git-diff) are really something we wanted to keep. So, we wanted also the GH repo to be up-to-date with the "production" (i.e. the dreamhost server) repo. 

I did not want to manually update the GitHub repository from time to time, neither was to have all the other users push also to it, along with the main server.

So I found the solution of my problems in this page (coincidentally, or maybe not, in the same website as before).

I rewrote the post-receive hook (which was already customized because we are using a bare git repository in another folder than the work tree) as follows:

	#! /bin/sh
	export GIT_WORK_TREE=~/bifrost.it
	git checkout -f
	nohup git push github &>/dev/null &

Note that the git repository is the folder `bifrost.it.git`, while the actual work tree is in the folder `bifrost.it` (both located in the home of the dreamhost user).

Now, every time a user pushes to the dreamhost server, also the github repository is updated. 

Neat!