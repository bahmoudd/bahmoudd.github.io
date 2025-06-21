+++
title = "Xlibre is the FOSS world in action"
description = "Why Xlibre is great news for the FOSS world"
summary = "A discussion about Xlibre and Wayland, and why a fork of X.org is so desparately needed"
date = 2025-06-21
draft = false
+++

![](/images/posts/xlibre/Wayland-Vs-Xorg.png)

As you all may know, Wayland has existed for 20-ish years and is still incomplete. Take, for example, accessibility. On-screen keyboards, for example, are pretty difficult to set up on Wayland compositors, to put it lightly.

The direction freedesktop is taking with Wayland is not the direction most people want regular display protocols to take. Many projects like Flatpak and Appimage try to unify the Linux desktop by providing a common packaging format that is compatible amongst most distros (well, the distros that people actually use, of course). 

By leaving pretty much everything to the compositor, like important functionality such as managing refresh rates, managing multiple monitors, setting specific resolutions .etc, this means that developers who want to make desktop environments have to write more boilerplate to get basic functionality out of the display server. Since distros are more likely to prefer one desktop environment over another, this means that basic things like setting resolution will be different from one distro to another. What the fuck, Wayland? This is going against many developers' efforts to unify the Linux desktop.

Since there's no simple command to change basic things, beginners will have to enter rabbit holes in order to find the one command that allows them to do things. Hence, why the "year of the Linux desktop" is being placed out of the reach of Linux users because of freedesktop.

The people that worked on X11 now work on Wayland. So, freedesktop has been trying to kill Wayland for some time now. Project developers killing good things is not what I signed up for when switching to Linux - it's exactly why I'm phasing Microsoft out of my life.

By forking X11 and creating Xlibre, Enrico Weigelt is essentially preserving the essence of the FOSS world - if a project dies out, fork it, and if that fork dies, fork that one and so on.

X11 was itself a fork of Xfree86. Xfree86 was forked because the people actually doing work on the project were being fucked over by the fellas leading the Xfree86 project. Now the same thing is happening between freedesktop and Weigelt. Refer to the image below.

![](/images/posts/xlibre/we_killed_xorg.png)
![](/images/posts/xlibre/bloody_wankers.png)

This "you will own nothing and you will be happy" mentality is not what I signed up for when installing Linux. Weigelt forking the X.org project is honestly doing the work that probably should have been done some time ago.

Changing the topic slightly, whilst I'm not a fan of Wayland, I'm pretty much forced to use it. Most drivers and new software is only gonna work on Wayland, and this is only going to get worse later on. Forking X11 is the first step in producing a usuable Linux desktop space. Now all we need is people to start making software and shit for X now, which might or might not happen. Only time will tell.