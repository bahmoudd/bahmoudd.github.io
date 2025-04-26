+++
title = 'Introduction'
showPagination = true
weight = 20
showDate = false
hideFromRecent = true
+++

# Requirements

You must have basic technical understanding (i.e. know what 'hardware' and 'software' mean) and a x86-64 computer, which your computer likely is. This guide will not cover how to install unofficial ports of Arch Linux, such as Artix, Arch Linux ARM or Arch Linux 32. Click on one of the collapsible sections below (depending on your operating system) to check if you have an x86-64 CPU.

{{< details summary="Switching to Arch from Windows?" >}}
Hit the Windows Key and R on your keyboard at the same time, a dialog like the below should appear on the bottom left of your screen:
![](/images/arch-install-guide/introduction/run_dialog.png)

In it, type `cmd.exe`, and hit enter.
A window like the below should appear:
![](/images/arch-install-guide/introduction/cmd.png)

In that, type `echo %PROCESSOR_ARCHITECTURE%` and hit enter.
If it returns `AMD64`, you're all good to go.
{{< /details >}}


# Important terminology

Important terminology can be found on the glossary [_here_](../glossary/). Make sure to have a good read of it so you have a good understanding of what I'm trying to across in the guide.

# Important thing to note

If you see a line like the below:
```$ ls```

Check the character in front of it, if it starts with a dollar sign, that means you type everything after the dollar sign, but not the dollar sign itself.\
For example:
```$ ls``` means that you should type ```ls``` into your shell, and not ```$ ls```

If you see a hash symbol, however, that means you should run the command with elevated privileges. If you're in the Arch ISO (i.e. not the operating system installed on your computer), then you don't need to do anything, type everything after the hash symbol.\
If Arch Linux is properly installed on your computer, and you are booted into it, you can do one of the two following things:

1) Run `sudo su` in to your shell before typing in to it, this allows you to run any privileged command you want. Make sure you type `exit` once you're done
2) Or, you can do the better method, which is, substitute the hashtag symbol for the word `sudo`, so something like:\
```# pacman -Syu``` means that you type ```sudo pacman -Syu``` into your shell.