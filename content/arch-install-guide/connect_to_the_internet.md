+++
title = 'Connect to the internet'
showPagination = true
invertPagination = true
weight = 30
showDate = false
+++

Now that you have entered the Arch [_live ISO_](/arch-install-guide/glossary/iso), you'll need to connect to the internet.\
You'll need to connect to the internet in order to download essential programs, such as the [_kernel_](/arch-install-guide/glossary/kernel).

There are two main ways to connect to the internet, and one is a lot more common than the other.

The first method is a fixed broadband, which is where your modem is connected to the wider-area network using a cable.\
The second method is a mobile broadband modem, where your modem is connected to the wider-area network using a cellular network (like the one your phone uses, 4G and 5G).

If you are unsure, you likely have a fixed broadband.\
If you normally connect via an ethernet cable, you may skip this section after plugging it in.

<details>
     <summary><span style="font-size:1.25em;">Connecting to a fixed broadband network</span></summary>

Firstly, enter the below command:
{{< highlight cmd >}} iwctl {{< /highlight >}}

This will change your [_shell_](/arch-install/guide/glossary/shell) prompt from:
{{< highlight cmd >}} root@archiso ~ # {{< /highlight >}}

to:

{{< highlight cmd >}} [iwd]# {{< /highlight >}}

In this new prompt, the following command will show a list of your network devices (interface that provides some network functionality, e.g. connecting to the internet using Wi-Fi) and their adapters (the actual network hardware):
{{< highlight cmd >}} [iwd]# device list {{< /highlight >}}

Find your network device (and its adapter, if applicable) from the list given, and turn them on using the commands below:
{{< highlight cmd >}} [iwd]# device {network device} set-property Powered on {{< /highlight >}}

{{< highlight cmd >}} [iwd]# device {network adapter} set-property Powered on {{< /highlight >}}

Once you have done that, scan for networks using the command below:
{{< highlight cmd >}} [iwd]# station {network device} scan {{< /highlight >}}

Take note that the above command will not output anything. To actually output a list of all the networks around your computer, run the following command:
{{< highlight cmd >}} [iwd]# station {network device} get-networks {{< /highlight >}}

Then, to connect to the network of your choice, use the below command:
{{< highlight cmd >}} [iwd]# station {network device} connect {network SSID} {{< /highlight >}}

If the network is hidden (i.e. it doesn't show up in the list of networks, but you want to connect to it anyway), use the below command:
{{< highlight cmd >}} [iwd]# station {network device} connect-hidden {network SSID} {{< /highlight>}}

Enter your network password when prompted and hit enter.

Once finished, simply enter:
{{< highlight cmd >}} [iwd]# exit {{< /highlight >}}
</details>


<details>
         <summary><span style="font-size:1.25em;">Connecting to a mobile broadband modem </span></summary>

Enable the `modemmanager` service, as shown below:

{{< highlight cmd >}} # systemctl enable modemmanager.service --now {{< /highlight >}}

`modemmanager` is the software that allows you to connect to your mobile broadband modem.

To get a list of all the mobile broadband modems around you, run the below command:
{{< highlight cmd >}} # mmcli -L {{< /highlight >}}

Look for ```/org/freedesktop/ModemManager1/Modem/[modem index]``` (where your modem index is the unique number representing your modem)

Connect to your modem by running:
{{< highlight cmd >}} # mmcli -m {modem index} --simple-connect="apn={your modem's APN}" {{< /highlight >}}

Your APN is your modem's Access Point Name and will have been given to you by your ISP.\
If your modem requires a username and password, you can specify them like so:\
{{< highlight cmd >}} mmcli -m {modem index} --simple-connect="apn={your modem's APN},user={username},password={password}" {{< /highlight >}}

</details>

Test that your internet connection actually works, as shown below:
{{< highlight cmd >}} ping -c 4 archlinux.org {{< /highlight >}}