+++
title = "Pre-chroot configuration"
summary = "Informs you on how to set up the mirrorlist, fstab file and how to install the bare minimum so that you can fully set up the operating system later"
showPagination = true
invertPagination = true
weight = 60
showDate = false
+++

Now that the internet and partitions have been fully sorted out, make sure that you get the faster download speeds possible.

### Enabling parallel downloads

Edit the `pacman.conf` file using the command below:
```
# nano /etc/pacman.conf
```

And uncomment the following line (meaning, remove the hashtag preceding the line):
```
#ParallelDownloads = 5
```

So that it becomes:
```
ParallelDownloads = 5
```

This single line means that, instead of downloading each package one at a time, it will downloads five at once.\
Hit `Ctrl`+`W` then `Enter` to save. Then hit `Ctrl`+`Q` to exit out of Nano.

### Setting up the mirrorlist

To create the mirrorlist, run the following command
```
reflector -c <your country> -a 12 -p https --sort rate --save /etc/pacman.d/mirrorlist
```

`-c` specifies the country that you live in. This is so that the mirrors have a low ping.\
`-a` specifies the "age" of the mirrors. The "age" is how long the mirrors have gone without being updated. A lower "age" normally means that the mirror gets updated more frequently.\
`-p` specifies the "protocol" of the mirrors, which means, how the packages are downloaded. Specifying "HTTPS" here means that your downloads are kept secure (i.e. not tampered with during the download).\
`--sort` specifies how the mirrors should be sorted. You will want to sort them by how fast the download rates are (for obvious reasons)\
`--save` specifies where this mirrorlist should be saved. `pacman` will check `/etc/pacman.d/mirrorlist` for the mirrorlist, so it makes sense to save it there.

### Installing the base system

You will want to install the bare minimum just so that you can install and configure things properly inside of your actual operating system. You can this using the `pacstrap` command shown below:
```
pacstrap -K /mnt base base-devel linux linux-firmware nano intel-ucode mtools dosfstools networkmanager
```

`base` is a minimal package set that defines a basic Arch Linux installation.

`base-devel` is a set of basic tools to build Arch Linux packages.

`linux` is the [_kernel_](/arch-install-guide/glossary/kernel) itself.

`linux-firmware` is a set of firmware files to assist the Linux kernel.

`nano` is a text editor, which will be used to edit configuration files later on. Feel free to replace this with `vim`, `neovim` or `emacs` if you are more familiar with those.

`intel-ucode` provides low-level firmware updates for Intel CPUs to fix bugs, security vulnerabilities and strange behaviour. If you use an AMD CPU instead, replace this with `amd-ucode`.

`mtools` allows you to access FAT [_filesystems_](/arch-install-guide/glossary/filesystem). This is helpful for if you want to plug in any USB drive or SD cards in to your computer. FAT (or File Allocation Table) is a family of filesystems that are common on external storage devices - the most common of which is FAT32.

`dosfstools` allows you to format and repair FAT filesystems.

`networkmanager` allows you to connect to the internet and manages things like Wi-FI, ethernet, VPNs, mobile broadband modems, proxies .etc

---

If you formatted your root/home partition(s) to btrfs, append the below package to the command:
```
btrfs-progs
```

`btrfs-progs` is a set of tools to help you manage btrfs filesystems on Linux.

However, if you formatted yout root/home partition(s) to ext4, append the below package to the command:
```
e2fsprogs
```

It does the same things that `btrfs-progs` except for ext4 filesystems instead of btrfs filesystems.

---

If you connected to the internet via `modemmanager`, go ahead and append the below packages to the command:
```
modemmanager usb_modeswitch
``` 

`modemmanager` allows you to connect the internet through a mobile broadband modem.

`usb_modeswitch` fixes an annoying problem when handling with mobile broadband modems. With certain mobile broadband modems plugged into the computer via USB, Linux sometimes mistakens these as storage devices instead of modems. This package fixes that problem by teling the modem, "stop pretending to be a CD, go into modem mode"


### Generating the fstab file

{{< notice warning >}}
This step is __CRUCIAL__. If you forget to do this step, your Arch Linux system will *not* boot.
{{< /notice >}}

Arch Linux will not remember where you have mounted your partitions.\
To make it remember, you will have to create an fstab file, which describes your drive's partitions and where to mount them to on boot.

This is done with the following command:
```
genfstab -U /mnt >> /mnt/etc/fstab
```

{{< notice note >}}
A `>` will overwrite a file and a `>>` will append to a file. Make sure you don't confuse these with each other
{{< /notice >}}