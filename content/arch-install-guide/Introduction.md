+++
title = 'Introduction'
showPagination = true
invertPagination = true
weight = 20
showDate = false
+++

Arch Linux is a [_rolling release_](/arch-install-guide/glossary/package-manager) [_Linux distribution_](/arch-install-guide/glossary/distro), meaning that software updates are released as small continuous updates rather than big updates delivered at regular intervals, like Windows. 

This makes Arch Linux great for gaming, as new updates to GPU drivers and such are installable as soon as they are available. 

However, there is a bit of a learning curve when it comes to Arch, especially when it comes to installing it and any apps through [_pacman_](/arch-install-guide/glossary/package-manager). However, don't let this scare you, as this guide will cover those things in-depth.

## Important terminology

Important terminology can be found on the glossary [_here_](../glossary/). Make sure to have a good read of it so you have a good understanding of what I'm trying to across in the guide.

## What this guide will not cover (as of now)

All the points below are unplanned as of now - but may come sometime in the future!

* How to install any unofficial ports of Arch Linux (e.g. Artix, Arch Linux ARM, Arch Linux 32 .etc).
* How to dual-boot any operating system with Linux
* How to configure desktop environments.
* How to configure [_shells_](/arch-install-guide/glossary/shell)
* How to configure greeters

## Requirements

You must have basic technical understanding (i.e. know what 'hardware' and 'software' mean) and you must have an AMD64 computer (or 'x86_64') which your computer likely is.

<details>
    <summary><span style="font-size:1.25em;">Switching to Arch from Windows (or want a dual-boot setup)?</span></summary>

Hit the Windows Key and R on your keyboard at the same time, a dialog like the below should appear on the bottom left of your screen:
![](/images/arch-install-guide/run_dialog.png)

In it, type `cmd.exe`, and hit enter.
A window like the below should appear:
![](/images/arch-install-guide/cmd.png)

In that, enter the below command:
```
echo %PROCESSOR_ARCHITECTURE% 
```
If it returns `AMD64`, you're all good to go.

</details>

<details>
    <summary><span style="font-size:1.25em;">Switching to Arch from MacOS or another Linux distro?</span></summary>

On MacOS, open the "Terminal" application from Finder.\
On any Linux distribution, open your terminal application. This could be kitty, alacritty, konsole, yakuake .etc.\
In the shell, enter the below command:
```
uname -m 
```
If it returns `x86_64`, you're all good to go.

</details>
 
</br>

## Guide notation

`<...>` means that there's something between the text shown in the guide, which have been omitted to narrow the guide's focus, or because the program lists something specific to your computer .etc

Anything else between angled brackets means that you should substitute it with what the text reads, for example, `<your drive>` means that you should substitute `<your drive>` for the drive that you want to install Arch Linux on to.

Any text after hashtags explain the command you are running and may be omitted when you type it in.

This means that if you see the below in the guide:
```
sfdisk --delete <your drive> # make a backup of your drive before running this command 
```

Assuming your drive is /dev/sda, you would type the below command into the shell:
```
sfdisk --delete /dev/sda 
```

### Prompts

`#` before a command means that you need the command as [_root_](/arch-install-guide/glossary/root-user) in order to execute it. The safest (and simplest) was to do so is to replace the hashtag with `sudo`. If you are in the Arch Live ISO, you can simply omit the hashtag when typing in the command.

`$` before a command means that the command can just be run normally. Just omit the dollar sign when typing in the command.

Any other prompt before a command means that you should not be typing in the command into your shell, but rather, you should be typing it into some other program, such as iwctl, which has the prompt: `[iwd]#`