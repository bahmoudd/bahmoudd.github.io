+++
title = "Booting the Arch Live ISO"
summary = "Informs you on how to boot into the Arch Live ISO and basic things like setting up keymaps and font sizes in the Live ISO"
showPagination = true
invertPagination = true
weight = 30
showDate = false
+++

### Reboot into firmware interface

Firstly, have a BitTorrent client installed on your computer. If you don't, install one from [here](https://www.qbittorrent.org/download).

Then, visit the official Arch Linux website to find the magnet link required to download the file. Once you find the magent link, click on it and the torrenting process should start shortly.

Once the torrenting process has completed, you should see a file named `archlinux-2025.05.01-x86_64.iso` in the downloads folder on your computer.

Take this file and use some program such as [Rufus](https://rufus.ie/en/) (Windows only), [BalenaEtcher](https://etcher.balena.io/#download-etcher) or [Ventoy](https://www.ventoy.net/en/download.html) to write the ISO image to an appropriate medium, such as a CD, SD card or USB thumbdrive.

Once you have written the ISO file to your computer, click on one of the collapsible sections below and follow the instructions given, depending on what browser you're starting off from:

<details>
    <summary><span style="font-size:1.25em;">Switching from Windows to Arch?</span></summary>

Hit the Windows Key and R on your keyboard at the same time, a dialog like the below should appear on the bottom left of your screen:                                    ![](/images/arch-install-guide/run_dialog.png)

In it, type `cmd.exe`, and hit enter.
A window like the below should appear:
![](/images/arch-install-guide/cmd.png)

In that, enter the below command:
```
$ shutdown /r /fw /t 1
```

You should see some kind of screen with options to configure how your computer runs. What exactly you see depends on your hardware manufacturer, which you should search up, as having a photo for each firmware options screen would make this page unnecessarily long.

Find some option with a name similar to `boot options`, and select the storage medium that contains the Arch Linux live environment.

---

</details>

<details>
    <summary><span style="font-size:1.25em;">Switching to Arch on a Mac?</span></summary>

Turn off your computer and hold the `Option` key as you turn on your Mac.\
You may see a screen like the below. If your computer boots normally, you held `Option` too late, so try again with better timing.
![](/images/arch-install-guide/macos-startup-manager.png)

Use the arrow keys on your keyboard to navigate to the option labelled `EFI Boot` and press `Enter` on your keyboard to select it.

---

</details>

<details>
     <summary><span style="font-size:1.25em;">Switching to Arch from another Linux distro?</span></summary>

Open your terminal application, this could be kitty, alacritty, konsole, yakuake .etc.\
In your shell, type the below command:
```
# systemctl reboot --firmware-setup
```

---

</details>

Once you have booted from your storage medium, select `Arch Linux install medium (x86_64, UEFI)`, or `Arch Linux install medium (x86_64, UEFI) with speech` if you are visually impaired.

You should then see something resembling the following screen:

![](/images/arch-install-guide/live_environment.png)

### Change font (on HiDPI monitors)

If you have a HiDPI monitor, it may be in your best interest to change the terminal font to a larger one since the text may be small and difficult to read.\
Load a larger terminal font as shown below:
```
setfont ter-132b
```

### Load keymaps

A keymap is how your keyboard is laid out. It defines the keys you use and where they are placed on the keyboard. To find a list of all the keymaps available for your language/region, run the below command:

```
localectl list-keymaps
```

To search for a keymap, use the following command, replacing `<search_term>` with the code for your language, country, or layout:
```
localectl list-keymaps | grep -i <search_term>
```

Once you've found a keymap that matches your physical keyboard's layout, run the below command.

```
loadkeys <keymap>
```