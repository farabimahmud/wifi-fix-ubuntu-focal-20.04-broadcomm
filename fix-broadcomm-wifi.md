# How to fix wifi network not found issue in Ubuntu LTS 20.04
In this fix I will try to give detailed step by step guide on how to fix the following issues of Ubuntu 20.04 LTS with Broadcomm adapters

1. wifi adapter not found
2. wifi network not found (etc.)


## Step 1: Check if you have the Ubuntu 20.04 version
This fix will work for Ubuntu 20.04 LTS version only. For other versions it would not work. 
1.1 Open Terminal by typing `ctrl + alt + t`
1.2 Type `lsb_release -a` and hit `enter`
1.3 If you see something like this then you are fine to proceed to next step
<pre>
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04 LTS
Release:	20.04
Codename:	focal
</pre>

## Step 2: Check if you have Broadcomm adapters
This fix will work for some specific models of Broadcomm wifi adapters with BC 43. For other variants of adapters this will not work. 
To check the version of your wifi adapter - 
2.1 Open Terminal by typing `ctrl + alt + t`
2.2 Type `lshw -c network` and hit `enter`
2.3 If you see something like this then you are fine to proceed to next step

<pre> *-network
       description: Wireless interface
       product: BCM43228 802.11a/b/g/n
       vendor: Broadcom Inc. and subsidiaries
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 00
       serial: xx:xx:xx:xx:xx:xx
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.30.223.271 (r587334) ip=x.x.x.x latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:f7d00000-f7d03fff
</pre>

Here you can see the wifi adapter model is **BCM43228**. This fix will work for any adapter with BCM43xxx series. 

## Step 3: Download the required packages and copy them locally. 
Now you need to download the followin required packages. 
You can either download them via wired connection or collect them from official ubuntu repository using another PC and copy them locally via USB drive.

You need to collect the following .deb packages via offline (usb drive) 
1. bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu5_amd64.deb [official mirror](http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu5_amd64.deb)
2. libc6-dev_2.31-0ubuntu9_amd64.deb [official mirror](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.31-0ubuntu9_amd64.deb)
3. libc6-dev_2.31-0ubuntu9_i386.deb  [official mirror](http://mirrors.kernel.org/ubuntu/pool/main/g/glibc/libc6-dev_2.31-0ubuntu9_i386.deb)
4. linux-libc-dev_5.4.0-42.46_amd64.deb [official mirror](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.4.0-42.46_amd64.deb)
5. linux-libc-dev_5.4.0-42.46_i386.deb [official mirror](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.4.0-42.46_i386.deb)

put all of these files in a separate folder named `driver-broadcomm`

## Step 4: Installing the driver
4.1 Now cd to the directory you created in previous step `cd ~/driver-broadcomm`
4.2 Install the files with the help of dpkg `sudo dpkg -i *.deb`
Your wifi adapter should be up and running now like a charm! 

Leave a comment/star if you find this helpful! 

