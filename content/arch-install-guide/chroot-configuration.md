+++
title = "Chroot configuration"
summary = "Informs you on how to set the time, date, locale, language, root password and any user accounts"
showPagination = true
invertPagination = true
weight = 70
showDate = false
+++

Enter into the Arch Linux system by typing the below command:

```
arch-chroot /mnt
```

### Set the date and time

To see what timezones are available, run the below command:
```
# ls /usr/share/zoneinfo/
```

Then, once you find your region, run the below command to narrow the timezone to cities
```
# ls /usr/share/zoneinfo/<region>
```

An example of a timezone path would be:
```
/usr/share/zoneinfo/Europe/London
```

Set the system's timezone to yours by running the below command:
```
# ln -sf /usr/share/zoneinfo/<region>/<city> /etc/localtime
```

Then, synchronise the hardware clock with the system clock:
```
# hwclock --systohc
```

### Set the locale and language

Open and edit the `/etc/locale.gen` file (as shown below):
```
# nano /etc/locale.gen
```

And then find your locale from the list shown on-screen.\
This will be your two-letter language code, followed by a dash, then your two-letter country code, then a character set.

The following links will help you:
https://en.wikipedia.org/wiki/List_of_ISO_639_language_codes
https://en.wikipedia.org/wiki/ISO_3166-2

An example of a locale would be:
```
#en_US.UTF-8 UTF-8
```

Once you've found your locale, uncomment it. This would turn the above into the below:
```
en_US.UTF-8 UTF-8
```

Save and quit (`Ctrl`+`W` then `Enter` then `Ctrl`+`Q`)

Once all of this is done, let Arch Linux recognise them by running the below command:
```
locale-gen
```

Then, open and edit the `/etc/locale.conf` file (as shown below):
```
# nano /etc/locale.conf
```

Add `LANG=` followed by the first part of your locale. So, given the above locale, add the following to the file:
```
LANG=en_US.UTF-8
```

If your keyboard layout is not an American English keyboard, run the below command:
```
# echo "KEYMAP=<your keymap>" > /etc/vconsole.conf
```

For example, a British person would run the below command:
```
# echo "KEYMAP=uk" > /etc/vconsole.conf
```

### Set the hostname

A hostname is what your computer identifies itself as when communicating to other computers. Set a hostname as shown below:
```
# echo <hostname> > /etc/hostname
```

You can set the hostname to whatever you like. Make sure you remember, because you'll need to when editing the hosts file.

### Editing the hosts file

Open and edit the `/etc/hosts` file (as shown below):
```
# nano /etc/hosts
```

Add the below lines to it:
```
127.0.0.1    localhost
::1          localhost
127.0.1.1    <your hostname>.localdomain <your hostname>
```

Save and quit (`Ctrl`+`W` then `Enter` then `Ctrl`+`Q`)

This step is important because a lot of programs tend to use `localhost` instead of `127.0.0.1`. The above step just translates `localhost` into `127.0.0.1`. `localhost` refers to the local machine on which a program is currently running on. It allows you to connect with services on the local machine's network without having to connect to an outer network.

### Enable networkmananger

"Enabling" a service essentially means to configure it so that it runs automatically at boot.\
NetworkManager configures things like Wi-FI, ethernet, VPNs, mobile broadband modems, proxies .etc, so it would make sense to enable it.

This is done by running the below command:
```
# systemctl enable NetworkManager
```

### Set the root password

Set a password for the [_root user_](/arch-install-guide/glossary/root-user) so that your computer isn't left wide open for cybercriminals to do as they please with your computer:
```
# passwd
```

### Create a user account

Doing this is common sense, as many greeters do not allow you to login to your desktop as the root user. To do this, run the below command:
```
# useradd -mG wheel <username>
```

`-m` option creates a user directory for you, where local configurations and apps are stored. 
`-G wheel` creates the user as part of the wheel group, which will allow you to make changes on the system itself. For example, downloading and installing packages, and configuring them.

Set a password for your user account (as shown below):
```
passwd [username]
```

Repeat the above process as many times as you want, depending on how many users you want to add to your system. If you do not want a user to make changes to the system, run the below command instead of the one shown above:
```
# useradd -m <username>
```

### Allow the 'wheel' group to make changes to the system

Open and edit the "`sudoers`" file (as shown below)
```
EDITOR=nano visudo
```

Find and uncomment the below line:
```
# %wheel ALL=(ALL:ALL) ALL
```

Save and quit (`Ctrl`+`W` then `Enter` then `Ctrl`+`Q`)