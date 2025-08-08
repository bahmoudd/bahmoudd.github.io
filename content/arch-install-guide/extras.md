+++
title = 'Extras'
summary = 'Informs you on different applications you can install/configure to make your Arch Linux experience more comfortable'
showPagination = true
invertPagination = true
weight = 100
showDate = false
+++

### Apps I would recommend installing

```
# pacman -S git openssh fastfetch lib32-mesa wine vlc audacious cups openssh tmux
```

Packages    | Description
----------- | ----------
openssh\*   | Secure Shell access server, allows you to access remote computers or servers. 
audacious   | Music player.
wget\*      | Wget is a free utility for non-interactive download of files from the Web. 
tmux        | A program that allows you to have multiple programs running in one terminal window.
git\*       | Allows you to interact with git [_repositories_](/arch-install-guide/glossary/repository) (needed to access the AUR) 
fastfetch   | Fastfetch is a command-line system information tool, that is the sucessor to NeoFetch. Used by Arch users to flex the fact that they have installed Arch.
cups\*      | Allows you to use printers
wine\*      | [_Compatibility layer_](/arch-install-guide/glossary/compatibility-layer) for Windows applications. Proton needs this application in order to run most Steam games
lib32-mesa\*| Allows you to run old 3D games on Steam

{{< notice note >}}
The programs marked wtih asterisks are some of the more important packages, which a lot of programs tend to rely on in order to work. It is highly recommended to install them.
{{< /notice >}}

#### Enable OpenSSH daemon and CUPS printer service
```
# systemctl enable sshd.service
# systemctl enable --now cups.service
```

</br>

### Installing Vulkan and OpenGL drivers

For pretty much any game to work, you need an OpenGL and a Vulkan driver. Check your GPU driver for the OpenGL and Vulkan drivers below:

GPU driver            | OpenGL driver                        | Vulkan driver                         |
--------------------- | ------------------------------------ | ------------------------------------- |
xf86-video-intel      | `mesa` & `lib32-mesa`                | `vulkan-intel` & `lib32-vulkan-intel`     |
xf86-video-amdgpu     | `mesa` & `lib32-mesa`                | `vulkan-radeon` & `lib32-vulkan-radeon`   |
xf86-video-ati        | `mesa` & `lib32-mesa`                | (N/A)                                 |
xf86-video-nouveau    | `mesa` & `lib32-mesa`                | `vulkan-nouveau` & `lib32-vulkan-nouveau` |
nvidia or nvidia-open | `nvidia-utils` & `lib32-nvidia-utils` | (Same as OpenGL drivers)               |

{{< notice note >}}
You'll want to install both the multilib (prefixed with lib32-*) and non-multilib drivers to ensure compatibility. Additionally, the drivers are listed by their name in the Arch Linux repositories - all the packages listed above can be installed as they are named above.
{{< /notice >}} 

### Installing an AUR helper

Most programs that run on Arch are found in the Arch User Repository. These are things like VS Code or the Brave browser.

To install programs from the AUR conveniently, you'll need to install an AUR helper. There are two good AUR helpers: yay and paru.

`yay` is great if you want a fast, no-fuss AUR helper.\
`paru` is better if you value safety, polish, and a nicer interface.

<details>
    <summary><span style="font-size:1.25em;">Installing paru</span></summary>

In order to install `paru`, you will need to have install `base-devel`. Ensure it is install by running the below command:
```
# pacman -S --needed base-devel
```

Then, install `paru` as shown below:
```
$ git clone https://aur.archlinux.org/paru.git && cd paru && makepkg -si
```

A guide on how to use `paru` can be found by running the below command:
```
man paru
``` 
And:
```
man paru.conf
```
---
</details>

<details>
    <summary><span style="font-size:1.25em;">Installing yay</span></summary>

In order to install `yay`, you will need to have install `base-devel`. Ensure it is install by running the below command:
```
# pacman -S --needed base-devel
```

Then, install `yay` as shown below:
```
$ git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```

A guide on how to use yay can be found [_here_](https://github.com/Jguer/yay?tab=readme-ov-file#examples-of-custom-operations)

---
</details>

### Enabling secure boot

Secure Boot is a security standard designed to ensure that a device boots using only trusted software. 

To enable it, go into your firmware settings and erase all of your secure boot keys. How to do so depends on your computer's manufacturer.

Once you've done that, install sbctl by running the below command:

```
# pacman -S sbctl
```

Then create secure boot keys by running the below command:
```
# sbctl create-keys
```

Then enroll those keys, alongside Microsoft's, to the UEFI
```
# sbctl enroll-keys -m
```

Check what files need to be signed by running:
```
# sbctl verify
```

If you have unified your kernel images, simply run the below command:
```
# sbctl sign -s /boot/EFI/Linux/arch-linux.efi
# sbctl sign -s /boot/EFI/Linux/arch-linux-fallback.efi
# sbctl sign -s /efi/EFI/BOOT/BOOTX64.EFI
```

If you haven't, then run the below commands instead:
```
# sbctl sign -s /boot/vmlinuz-linux
# sbctl sign -s /boot/EFI/Boot/bootx64.efi
# sbctl sign -s /boot/EFI/systemd/systemd-bootx64.efi
```

</br>

### Alternative shells

The shell that comes with your system automatically is bash. However, bash isn't very good. To fix that, you can use an alternative shell. Some will be listed below:

`zsh` is fully backwards compatible with bash, and is highly configurable shell. However, it has quite a learning curve.

`fish` is an easy-to-learn and highly configurable shell. It has features like autosuggestions out of the box. However, if you're used to bash or zsh, it might take some time to learn fish.

To see what shell you have as default (this will likely be bash), run the below command:
```
echo $SHELL
```

To see what shells you have installed on your system, run the below command:
```
chsh -l
```

Find the shell of your preference within that list and change it accordingly using the below command:
```
chsh -s <shell>
```

> Replacing ```<shell>``` with the shell of your preference. An example can be found below.

```
chsh -s /usr/bin/fish
```

<br/>