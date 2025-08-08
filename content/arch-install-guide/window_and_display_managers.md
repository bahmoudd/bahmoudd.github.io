+++
title = 'Window and display managers'
summary = 'Informs you on how to choose and install a window manager and a display manager'
showPagination = true
invertPagination = true
weight = 90
showDate = false
+++

### What is a window manager?

Put simply, a window manager organises your windows and decides how GUI elements are placed.\
There are two main types of Window Managers (WMs):
- Stacking Window Managers (SWMs)
- Tiling Window Managers (TWMs)

An SWM is your vanilla window manager. You use your mouse to stack, arrange and rearrange windows. There's normally a system tray, and a button to minimise all apps to it.

A TWM is a bit more advanced tham an SWM. Their main focus is to increase productivity by keeping your hands on the keyboard.\
→ There's keybinds for all functions, however, they have a much steeper learning curve.

### My advice?

Use a stacking window manager if you use the Nano text editor, and use a tiling window manager if you use Vim, Neovim or Emacs.

### Different SWMs

This section will cover Stacking Window Managers.

<details>
  <summary><span style="font-size:1.5em;">KDE Plasma</span></summary>

![](/images/arch-install-guide/kde-plasma.png)

To just install KDE Plasma, use the below command:
```
# pacman -S plasma
```

The packages below provide a more integrated desktop experience for KDE Plasma

```
# pacman -S konsole dolphin ark kwrite kcalc spectacle krunner partitionmanager
```

Packages         | Description
---------------- | ------------------------------------
plasma           | KDE Plasma window manager.
konsole          | Terminal.
dolphin          | File manager.
ark              | Archiving Tool.
kwrite           | Text editor.
kcalc            | Scientific calculator.
spectacle        | Screenshot capture utility.
krunner          | Quick drop-down desktop search.
partitionmanager | Disk & partition manager.
</details>
</br>
<details>
  <summary><span style="font-size:1.5em;">GNOME</span></summary>

![](/images/arch-install-guide/GNOME_Shell.png)

To install GNOME, use the below command:
```
# pacman -S gnome gnome-extra
```

```gnome-extra``` is for a more integrated desktop experience, and includes a bundle of apps to facilitate that.
</details>
</br>
<details>
  <summary><span style="font-size:1.5em;">Enlightenment</span></summary>

![](/images/arch-install-guide/Enlightenment.png)

Install Enlightenment, as shown below:
```
# pacman -S enlightenment ecrire ephoto evisum rage terminology
```

The packages that aren't `enlightenment` provide a more integrated desktop environment.

Packages         | Description
---------------- | ------------------------------------
enlightenment    | Enlightenment window manager
terminology      | Terminal
ecrire           | Text editor
evisum           | Process viewer, similar to Task Manager on Windows
ephoto           | Photo viewer
rage             | Video viewer

</details>
</br>
> Note: Wayland support on LXQt and XFCE is a bit shaky.

<details>
  <summary><span style="font-size:1.5em;">LXQt</span></summary>

![](/images/arch-install-guide/lxqt.png)

To install LXQt, use the below command:
```
# pacman -S lxqt
```
</details>
</br>
<details>
  <summary><span style="font-size:1.5em;">XFCE</span></summary>

![](/images/arch-install-guide/xfce.png)

To install XFCE, use the below command:
```
# pacman -S xfce xfce4-goodies
```

```xfce4-goodies``` is for a more integrated desktop experience, and includes a bundle of apps to facilitate that.

</details>

### Different TWMs

> Images used are meant to demonstrate their customisability and do not reflect what they look like out-of-the-box.

<details>
  <summary><span style="font-size:1.5em;">Hyprland</span></summary>

![](/images/arch-install-guide/hyprland.png)

To install hyprland, use the below command:
```
# pacman -S hyprland
```
</details>
</br>


<details>
  <summary><span style="font-size:1.5em;">Niri</span></summary>

![](/images/arch-install-guide/niri.png)

Install Niri, as shown below:
```
# pacman -S niri
```
</details>
</br>
<details>
  <summary><span style="font-size:1.5em;">Sway</span></summary>

![](/images/arch-install-guide/swaywm.png)

Install Sway, as shown below:
```
# pacman -S sway swaylock swaybg swayidle
```

</details>
</br>
<details>
  <summary><span style="font-size:1.5em;">river</span></summary>

![](/images/arch-install-guide/river.png)

To install river, use the below command:
```
# pacman -S river
```

</details>

