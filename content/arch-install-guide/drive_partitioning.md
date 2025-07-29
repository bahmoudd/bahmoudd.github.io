+++
title = "Partitioning the drive"
summary = "Informs you on what partitions to make, how to make them, and how to format and mount them"
showPagination = true
invertPagination = true
weight = 50
showDate = false
+++

Now that the Arch [_live ISO_](/arch-install-guide/glossary/iso) has been connected to the internet, you'll need to divide your disk up into [_partitions_]().

This guide will show you how to create four different partitions:
* A boot partition, which holds the files that load the [_kernel_](/arch-install-guide/glossary/kernel) and other necessary things for your computer to enter a state where it can be used.
* A swap partition, which holds [_swap space_](/arch-install-guide/glossary/swap)
* A root partition, which holds your [_root directory_](/arch-install-guide/glossary/root-directory.md)
* A home partition, which holds your user account and anything that might be stored on to it, like images and documents.

{{< notice warning >}}
The guide assumes you want to delete everything on your drive.\
Make sure you have backed up everything important on it before you continue with this guide.
{{< /notice >}}

### Partitioning the drive

Firstly, enter the gdisk [_shell_](/arch-install-guide/glossary/shell) (which is a program that helps you manage modern drives), as shown below:
```
# gdisk <your drive>
```

This will change your shell prompt from:
```
root@archiso ~ # 
```

to
```
Command (? for help):
```

Enter "expert mode" as shown below (expert mode allows you to do more things with your drive):
```
Command (? for help): x
```

Which changes your prompt to this:

```
Expert command (? for help):
```

Delete everything on your drive using the below command:
```
Expert command (? for help): z
```

This will bring up a warning message to confirm this is *absolutely, positively* what you want to do.\
Enter "y" to confirm.
```
About to wipe out GPT on {your drive}. Proceed (Y/N): y
```

Another message will pop up:
```
GPT data structures destroyed! You may now proceed to partition the disk using fdisk or other utilities.
Blank out MBR? (Y/N):
```

Enter "y" to confirm the above. This will overwrite the first 512 bytes of your drive so that any bootloader you install later on will not get confused.

After clearing your drive, gdisk will return you to your regular shell prompt (as seen below):
```
root@archiso ~ # 
```

Return to the gdisk shell by entering:
```
# gdisk <your drive>
```

Changing your prompt back to:
```
Command (? for help):
```

You will want to create partitions for Arch Linux to live on.
This can easily be done by entering the following commands.

Firstly, you want to create a boot partition (as shown below):
```
Command (? for help): n
```

gdisk will then ask you what number you want to give this partition, as shown below.
```
Partition number (1-128, default 1): 
```

Simply press enter when it prompts you with the above. Here, gdisk just gives the partition the next unused number.

Next, gdisk will ask you where you want the partition to begin.
```
First sector (<...>, default=2048) or {+-}size{KMGTP}: 
```

Press enter to begin the partition at the first bit of free space it can allow.

Then, gdisk will ask how big you want the partition to be (as shown below).\
1 gigabyte is more than enough for a boot partition.

```
Last sector (<...>, default=<...>) or {+-}size{KMGTP}: +1G
```

It will then ask you what type of partition you want to create.\
We want to create a modern boot partition. So enter 'EF00' as shown below.
```
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): EF00
```

It will then return you to:
```
Command (? for help):
```

You will want to set a "label" for this partition - a unique name to help you identify this partition.\
For the purposes of this guide, it will be labelled as "boot"

```
Command (? for help): c
```

gdisk will then ask you which partition you want to label. Select partition `1`

```
Partition number (1-1): 1
```

Then it will ask you to set the label for this partition. Enter `boot`
```
Enter name: boot
```


This time, you will want to create a swap partition.\
Create a new partition as shown below.

```
Command (? for help): n
```

gdisk will then ask you what number you want to give this partition, as shown below.\
Hit enter to use the default.

```
Partition number (2-128, default 2): 
```

Next, gdisk will ask you where you want the partition to begin.\
Hit enter to use the default.
```
First sector (<...>, default=<...>) or {+-}size{KMGTP}: 
```

Then, gdisk will ask you how big you want the partition to be.\
The size of this partition will depend on how big your RAM is. Make your swap partition twice the size of your RAM, or use 16 gigabytes, whichever is smaller.\
The below is for if your RAM is 16 gigabytes or larger.

```
Last sector (<...>, default=<...>) or {+-}size{KMGTP}: +16G
```

It will then ask you what type of partition you want to create.\
We want to create a swap partition. So enter '8200' as shown below.
```
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300): 8200
```

Now, you will want to name this partition `swap`.\
```
Command (? for help): c
```

Enter the number for the swap partition (2):
```
Partition number (1-2): 2
```

Then name it `swap`
```
Enter name: swap
```

Now, you want to create a partition for your system files to live in (your root partition)
```
Command (? for help): n
```

Press enter to the below prompts to use their defaults:
```
Partition number (3-128, default 3): 
```
And:
```
First sector (<...>, default=<...>) or {+-}size{KMGTP}: 
```

Now for the size of your root partition. If your drive is small (less than 128GB), press enter to the below prompt to use up the rest of your drive. This will mean that your system files and things like documents will live in the same space on your drive.

```
Last sector (<...>, default=<...>) or {+-}size{KMGTP}:
```

If your drive is 128GB in size or higher, then give your root partition 40GB in space.

```
Last sector (<...>, default=<...>) or {+-}size{KMGTP}: +40G
```

Simply press enter when given the below prompt, to tell your computer that this is just a regular filesystem partition.

```
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300):
```

Now, you will want to name this partition `root`.
```
Command (? for help): c
```

Enter `3` to the below prompt to select the root partition.
```
Partition number (1-3): 3
```

Then, name it `root`.
```
Enter name: root
```

<details>
         <summary><span style="font-size:1.25em;"> If you have a large drive </span></summary>

You also want to create a home partition for the files that are not boot, not root and not swap to live in.
```
Command (? for help): n
```

Press enter to the below prompts to use their defaults:
```
Partition number (4-128, default 4): 
```
And:
```
First sector (<...>, default=<...>) or {+-}size{KMGTP}: 
```
And the below (which tells gdisk to make the partition use up the rest of your drive):
```
Last sector (<...>, default=<...>) or {+-}size{KMGTP}:
```
And:
```
Current type is 'Linux filesystem'
Hex code or GUID (L to show codes, Enter = 8300):
```

You will want to name this partition `home`.
```
Command (? for help): c
```

Enter `4` to the below prompt to select the home partition.
```
Partition number (1-4): 4
```

Then name it `home`
```
Enter name: home
```

---

</details>

These partitions have been created, but have not actually been written to the drive.\
gdisk has only kept track of them in memory.\
To actually write them to drive, enter the below command:
```
Command (? for help): w
```

gdisk will confirm with you to ensure that you want to write these partitions to your drive.\
Enter `y` to confirm these changes.

```
Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING PARTITIONS!!

Do you want to proceed? (Y/N): y
```

You should then see the following message:

```
OK; writing new GUID partition table (GPT) to <your drive>
The operation has completed successfully
```

Then you will be returned to the shell prompt (see below)

```
root@archiso ~ # 
```

</br>

### Formatting partitions

Now that these partitions have been created, it is now time to make them actually useable.\
To do this, you will have to [_format_](/arch-install-guide/glossary/format) the partitions.

For most users, there are two filesystems that you can format your root (and home, if applicable) partition(s) to: btrfs and ext4.

Btrfs offers snapshots and checksumming. Snapshots are like freeze-frames of your entire [_filesystem_](/arch-install-guide/glossary/filesystem) so that if you screw something up, you can easily restore your files to how they were to some point in time before you screwed things up.

Checksumming just ensures that your data hasn't been maliciously tampered with.

ext4 doesn't have these things, but it is quite fast and is the most common filesystem you will find on Linux.

Check that your partitions are correct by typing in the below command:
```
lsblk
```

Format the boot partition, as shown below:
```
mkfs.fat -F32 /dev/disk/by-partlabel/boot
```

Then, format the swap partition, as shown below:
```
mkswap /dev/disk/by-partlabel/swap
```

<details>
    <summary><span style="font-size:1.25em;">If you want to encrypt your drive</span></summary>

If you want to encrypt your drive, namely your root and home partitions, you will have to set up LUKS encryption, which this guide will go over.

Firstly, ensure that your swap and boot partitions have been formatted.\
Then, start by encrypting your root partition, as shown below:
```
cryptsetup luksFormat /dev/disk/by-partlabel/root
```

cryptsetup will give you a warning, and ask for confirmation before encrypting your drive.\
To confirm, simply type `YES` in all caps as shown below.
```
WARNING!
========
This will overwrite data on /dev/disk/by-partlabel/root irrevocably.

Are you sure? (type 'yes' in capital letters): YES
```

cryptsetup will then ask you to set a passphrase. You should set a strong passphrase, preferably with a range of lower and upper case letters, numbers and punctuation. Make sure it is memorable too, because if you do not remember this, your root partition will permanently inaccessible.
```
Enter passphrase:
```

Then, it will ask you to verify this passphrase:
```
Verify passphrase:
```

Then, it will start encrypting your root partition, which may take a while.

Then, you will want to encrypt your home partition.
```
cryptsetup luksFormat /dev/disk/by-partlabel/home
```

cryptsetup will ask you for a passphrase, this can be the same as the passphrase you used for your root partition.
```
Enter passphrase:
```

Then, it will ask you to verify this passphrase:
```
Verify passphrase:
```

Then, it will start encrypting your home partition, which may take a while.

Now, in order to install anything on to your root and home partitions, you will have to open them, as shown below:
```
cryptsetup open /dev/disk/by-partlabel/root cryptroot
```

It will then ask you for your passphrase:
```
Enter passphrase for /dev/disk/by-partlabel/root:
```

Do the same for your home partition:
```
cryptsetup open /dev/disk/by-partlabel/home crypthome
```

It will then ask you for your passphrase:
```
Enter passphrase for /dev/disk/by-partlabel/home:
```

Now that the root and home partitions have been opened, it is time to format them.
Then, format the root partition, as shown below:

```sh
mkfs.btrfs /dev/mapper/cryptroot -f
# OR, do not run the below command if you have run the one above, or vice versa.
mkfs.ext4 -F /dev/mapper/cryptroot
```

If you have created a home partition, go ahead and format it.

```sh
mkfs.btrfs /dev/mapper/crypthome -f
# OR, do not run the below command if you have run the one above, or vice versa.
mkfs.ext4 -F /dev/mapper/crypthome

```

Once you have done all of the above, go ahead and skip to `If you have encrypted your root and home partitions` under `Mounting partitions`

---

</details>

Then, format the root partition, as shown below:

```sh
mkfs.btrfs /dev/disk/by-partlabel/root -f
# OR, do not run the below command if you have run the one above, or vice versa.
mkfs.ext4 -F /dev/disk/by-partlabel/root
```

If you have created a home partition, go ahead and format it.

```sh
mkfs.btrfs /dev/disk/by-partlabel/home -f
# OR, do not run the below command if you have run the one above, or vice versa.
mkfs.ext4 -F /dev/disk/by-partlabel/home
```


</br>

### Mounting partitions

For the partitions to be accessible to the Arch ISO, you need to mount them, which means to make them an accessible location on the Arch ISO.

<details>
    <summary><span style="font-size:1.25em;">If you have encrypted your root and home partitions</span></summary>

Start by mounting the root partition:
```
mount /dev/mapper/cryptroot /mnt
```

Then, mount the swap partition:
```
swapon /dev/disk/by-partlabel/swap
```

Then, mount the boot partition:
```
mount -m /dev/disk/by-partlabel/boot /mnt/boot
```

Finally, mount the home parititon:
```
mount -m /dev/mapper/crypthome /mnt/home
```

Once you've finished all of the above, you've finished with this page of the guide. Move on with the next page.

---
</details>

To do this, start by mounting the root partition.
```
mount /dev/disk/by-partlabel/root /mnt
```

Then mount your swap partition:
```
swapon /dev/disk/by-partlabel/swap
```

Then the boot partition:
```
mount -m /dev/disk/by-partlabel/boot /mnt/boot
```

And finally, the home partition:
```
mount -m /dev/disk/by-partlabel/home /mnt/home
```