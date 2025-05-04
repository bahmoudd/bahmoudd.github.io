+++
title = 'Introduction'
showPagination = true
invertPagination = true
weight = 20
showDate = false
+++

# What is Arch Linux?

Arch Linux is a rolling release Linux distribution, meaning that software updates are released as small updates released continuously rather than as big updates at regular intervals. This makes Arch Linux great for gaming, as new updates to GPU drivers and such are installable as soon as they are available. Also, there is a bit of a learning curve when it comes to Arch, especially when it comes to installation and installing apps through pacman. However, don't let this scare you, as this guide will cover those things in-depth.

# Important terminology

Important terminology can be found on the glossary [_here_](../glossary/). Make sure to have a good read of it so you have a good understanding of what I'm trying to across in the guide.

# Requirements

You must have basic technical understanding (i.e. know what 'hardware' and 'software' mean) and a x86-64 computer, which your computer likely is. This guide will not cover how to install unofficial ports of Arch Linux, such as Artix, Arch Linux ARM or Arch Linux 32. Click on one of the collapsible sections below (depending on your operating system) to check if you have an x86-64 CPU.

<details>
    <summary><span style="font-size:1.25em;">Switching to Arch from Windows (or want a dual-boot setup)?</span></summary>

Hit the Windows Key and R on your keyboard at the same time, a dialog like the below should appear on the bottom left of your screen:
![](/images/arch-install-guide/run_dialog.png)

In it, type `cmd.exe`, and hit enter.
A window like the below should appear:
![](/images/arch-install-guide/cmd.png)

In that, enter the below command:
{{< highlight cmd >}} echo %PROCESSOR_ARCHITECTURE% {{< /highlight >}}
If it returns `AMD64`, you're all good to go.

</details>

<details>
    <summary><span style="font-size:1.25em;">Switching to Arch from MacOS or another Linux distro?</span></summary>

On MacOS, open the "Terminal" application from Finder.\
On any Linux distribution, open your terminal application. This could be kitty, alacritty, konsole, yakuake .etc.\
In the shell, enter the below command:
{{< highlight bash >}} uname -m {{< /highlight >}}
If it returns `x86_64`, you're all good to go.

</details>
 
</br>

# Guide notation

`[...]` means that there's something between the two or more lines shown in the guide, which have been omitted to narrow the guide's focus.\
Anything else between square brackets means that you should substitute it with what the text reads, for example, `[your drive]` means that you should substitute `[your drive]` for the drive that you want to install Arch Linux on to.\
Any text after hashtags explain the command you are running and may be omitted when you type it in.

This means that if you see the below in the guide:
{{< highlight sh >}} sfdisk --delete [your drive] # make a backup of your drive before running this command {{< /highlight >}}
Assuming your drive is /dev/sda, you would type the below command into the shell:
{{< highlight sh >}} sfdisk --delete /dev/sda {{< /highlight >}}