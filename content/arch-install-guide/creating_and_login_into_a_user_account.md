+++
title = "Logging into your user account"
summary = "Informs you on how to install the programs that allow you to have a comfortable desktop experience and how to set up pacman and networking so that they can be used properly."
showPagination = true
invertPagination = true
weight = 80
showDate = false
+++

Now that Arch Linux has been fully installed on to your drive, it's time to make it a comfortable desktop experience.\
To do this, exit out of chroot, as shown below:
```
# exit
```

Then, reboot your computer:
```
# reboot
```

Once Arch Linux has booted, enter "root" as the username, and enter the root password when prompted.\

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

Save and quit (`Ctrl`+`O` then `Enter` then `Ctrl`+`X`).

Then, log out of `root`:
```
exit
```

### Re-connect to the internet

{{< notice note >}}
If you normally connect to the internet via ethernet, you may skip this section. 
{{< /notice >}}

Enter the username for your user account and the password for it when prompted.\
Once you have logged in, you must reconnect to the internet.

This is because the Arch ISO connected to the internet via `iwd` and the Arch installation connects to the internet through `network-manager`, which means that your network settings have been lost.

If you connected to the internet in the Arch ISO through a mobile broadband modem, the steps for connecting to the internet are [_the same as before_](/arch-install-guide/connect_to_the_internet). However, if you connected to the internet via a fixed broadband network, follow the steps shown below. 


Firstly, turn on Wi-Fi (as shown below):
```
$ nmcli r wifi on
```

And then list the access points that your computer can connect to:
```
$ nmcli d wifi list
```

Then, connect to the access point as shown below:
```
$ nmcli d wifi connect <access point SSID> password <access point password>
```

If your access point is not broadcasting its SSID, run the below command instead:
```
$ nmcli d wifi connect <access point SSID> password <access point password> hidden yes
```