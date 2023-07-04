---
title: "Operating system installation"
date: 2023-07-04T08:39:45+02:00
draft: false
weight: 3
objective: 711.1
---

In this first section we will cover the installation of the three major BSD flavours, as well as the process to upgrade them.
Let's get started!

## Installing OpenBSD
We must first download an installation image from <a href="https://www.openbsd.org/" target="_new">openbsd.org</a>.
In the menu on the left, you can click on Download, which brings you to the web page containing the available media.
There are several images available, depending on the installation media you want to use (USB flash drive, CD or DVD, or even a floppy disk).
At the time of writing the most recent version is version 7.0 but I want to install an older version so we can also discuss upgrading OpenBSD later.
To find an older version, we must go to one of the mirror sites of which you can find the link below the table.
I select a mirror, e.g. Fastly, then choose 6.9/amd64/install69.iso as I want to install OpenBSD using a DVD drive on an amd64 architecture.

Either you now burn the ISO image to a CD/DVD drive or you write the image file to a USB flash drive, or &mdash; as is the case for my setup &mdash; you create a new virtual machine and point the CD-ROM drive to the ISO file.
Boot the (virtual) system and the installation process can begin.

The output below is taken from the console during the installation process.
When I selected the default answer, I just pressed enter so the output only shows the default option between square brackets.
When I did not select the default option, you see some text after the default option between square brackets.
For example, when the question gets asked to create a user account, I picked the default option (no) while when the question got asked to allow root login via SSH, I answered "yes" instead of accepting the default option.

{{< highlight Bash >}}
erase ^?, werase ^W, kill ^U, intr ^C, status ^T

Welcome to the OpenBSD/amd64 6.9 installation program.
(I)nstall, (U)pgrade, (A)utoinstall or (S)hell? i
At any prompt except password prompts you can escape to a shell by
typing '!'. Default answers are shown in []'s and are selected by
pressing RETURN.  You can exit this program at any time by pressing
Control-C, but this can leave your system in an inconsistent state.

Terminal type? [vt220]
System hostname? (short form, e.g. 'foo') puffy.bsdspecialist.org

Available network interfaces are: vio0 vlan0.
Which network interface do you wish to configure? (or 'done') [vio0]
IPv4 address for vio0? (or 'dhcp' or 'none') [dhcp]
vio0: 192.168.0.239 lease accepted from 192.168.0.1 (38:43:7d:e5:17:fa)
IPv6 address for vio0? (or 'autoconf' or 'none') [none]
Available network interfaces are: vio0 vlan0.
Which network interface do you wish to configure? (or 'done') [done]
Using DNS domainname bsdspecialist.org
Using DNS nameservers at 195.130.131.3 195.130.130.3

Password for root account? (will not echo)
Password for root account? (again)
Start sshd(8) by default? [yes]
Change the default console to com0? [yes]
Available speeds are: 9600 19200 38400 57600 115200.
Which speed should com0 use? (or 'done') [9600]
Setup a user? (enter a lower-case loginname, or 'no') [no]
Since no user was setup, root logins via sshd(8) might be useful.
WARNING: root is targeted by password guessing attacks, pubkeys are safer.
Allow root ssh login? (yes, no, prohibit-password) [no] yes

Available disks are: sd0.
Which disk is the root disk? ('?' for details) [sd0]
No valid MBR or GPT.
Use (W)hole disk MBR, whole disk (G)PT or (E)dit? [whole]
Setting OpenBSD MBR partition to whole sd0...done.
The auto-allocated layout for sd0 is:
#                size           offset  fstype [fsize bsize   cpg]
  a:           614.6M               64  4.2BSD   2048 16384     1 # /
  b:           480.0M          1258688    swap
  c:         20480.0M                0  unused
  d:           863.3M          2241728  4.2BSD   2048 16384     1 # /tmp
  e:          1287.9M          4009792  4.2BSD   2048 16384     1 # /var
  f:          2429.1M          6647360  4.2BSD   2048 16384     1 # /usr
  g:           662.7M         11622240  4.2BSD   2048 16384     1 # /usr/X11R6
  h:          2417.7M         12979520  4.2BSD   2048 16384     1 # /usr/local
  i:          1485.8M         17930976  4.2BSD   2048 16384     1 # /usr/src
  j:          5491.7M         20973952  4.2BSD   2048 16384     1 # /usr/obj
  k:          4740.6M         32220864  4.2BSD   2048 16384     1 # /home
Use (A)uto layout, (E)dit auto layout, or create (C)ustom layout? [a]
/dev/rsd0a: 614.6MB in 1258624 sectors of 512 bytes
4 cylinder groups of 153.64MB, 9833 blocks, 19712 inodes each
/dev/rsd0k: 4740.6MB in 9708768 sectors of 512 bytes
24 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/rsd0d: 863.3MB in 1768064 sectors of 512 bytes
5 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/rsd0f: 2429.1MB in 4974880 sectors of 512 bytes
12 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
newfs: reduced number of fragments per cylinder group from 84824 to 84152 to
enlarge last cylinder group
/dev/rsd0g: 662.7MB in 1357280 sectors of 512 bytes
5 cylinder groups of 164.36MB, 10519 blocks, 21056 inodes each
/dev/rsd0h: 2417.7MB in 4951456 sectors of 512 bytes
12 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/rsd0j: 5491.7MB in 11246912 sectors of 512 bytes
28 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/rsd0i: 1485.8MB in 3042976 sectors of 512 bytes
8 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/rsd0e: 1287.9MB in 2637568 sectors of 512 bytes
7 cylinder groups of 202.50MB, 12960 blocks, 25920 inodes each
/dev/sd0a (a8f0f36513e3535b.a) on /mnt type ffs (rw, asynchronous, local)
/dev/sd0k (a8f0f36513e3535b.k) on /mnt/home type ffs (rw, asynchronous, local,
nodev, nosuid)
/dev/sd0d (a8f0f36513e3535b.d) on /mnt/tmp type ffs (rw, asynchronous, local,
nodev, nosuid)
/dev/sd0f (a8f0f36513e3535b.f) on /mnt/usr type ffs (rw, asynchronous, local,
nodev)
/dev/sd0g (a8f0f36513e3535b.g) on /mnt/usr/X11R6 type ffs (rw, asynchronous,
local, nodev)
/dev/sd0h (a8f0f36513e3535b.h) on /mnt/usr/local type ffs (rw, asynchronous,
local, nodev)
/dev/sd0j (a8f0f36513e3535b.j) on /mnt/usr/obj type ffs (rw, asynchronous,
local, nodev, nosuid)
/dev/sd0i (a8f0f36513e3535b.i) on /mnt/usr/src type ffs (rw, asynchronous,
local, nodev, nosuid)
/dev/sd0e (a8f0f36513e3535b.e) on /mnt/var type ffs (rw, asynchronous, local,
nodev, nosuid)

Let's install the sets!
Location of sets? (cd0 disk http nfs or 'done') [cd0]
Pathname to the sets? (or 'done') [6.9/amd64]

Select sets by entering a set name, a file name pattern or 'all'. De-select
sets by prepending a '-', e.g.: '-game*'. Selected sets are labelled '[X]'.
    [X] bsd           [X] comp69.tgz    [X] xbase69.tgz   [X] xserv69.tgz
    [X] bsd.rd        [X] man69.tgz     [X] xshare69.tgz
    [X] base69.tgz    [X] game69.tgz    [X] xfont69.tgz
Set name(s)? (or 'abort' or 'done') [done]
Directory does not contain SHA256.sig. Continue without verification? [no] yes
Installing bsd          100% |**************************| 20423 KB    00:01
Installing bsd.rd       100% |**************************|  4107 KB    00:00
Installing base69.tgz   100% |**************************|   291 MB    00:30
Extracting etc.tgz      100% |**************************|   254 KB    00:00
Installing comp69.tgz   100% |**************************| 85958 KB    00:11
Installing man69.tgz    100% |**************************|  7560 KB    00:01
Installing game69.tgz   100% |**************************|  2741 KB    00:00
Installing xbase69.tgz  100% |**************************| 29789 KB    00:03
Extracting xetc.tgz     100% |**************************|  7101       00:00
Installing xshare69.tgz 100% |**************************|  4502 KB    00:00 ETA
Installing xfont69.tgz  100% |**************************| 39342 KB    00:04
Installing xserv69.tgz  100% |**************************| 18351 KB    00:02
Location of sets? (cd0 disk http nfs or 'done') [done]

What timezone are you in? ('?' for list) [Canada/Mountain] Europe/Brussels
Saving configuration files... done.
Making all device nodes... done.
Relinking to create unique kernel... done.

CONGRATULATIONS! Your OpenBSD install has been successfully completed!

When you login to your new system the first time, please read your mail
using the 'mail' command.

Exit to (S)hell, (H)alt or (R)eboot? [reboot] halt
syncing disks... done

The operating system has halted.
Please press any key to reboot.
{{< /highlight >}}

The default installation process is pretty straightforward.
You can customize the installation easily by selecting different options.
The installation provides the necessary guidenace.

Before we move on to the installation of FreeBSD, let's check the OpenBSD version.

{{< highlight bash >}}
puffy# uname -a
OpenBSD puffy.bsdspecialist.org 6.9 GENERIC#464 amd64
{{< /highlight >}}

## Installing FreeBSD
FreeBSD presents us with a few more options to get a system up and running.
We can opt for the installation images, similar to OpenBSD, or we can opt for pre-installed images suitable for quickly getting started with FreeBSD on a virtual machine or Raspberry Pi or similar ARM board.
I will, once again, go for the installation ISO for the amd64 architecture.
You can pick your preferred installation method at <a href="https://www.freebsd.org/" target="_new">freebsd.org</a> and clicking the big yellow "Download FreeBSD" button.
I will once again take a release which is not the latest so that I can upgrade to the latest release.
Currently this is version 12.3 while the latest version is 13.0.

You might have noticed that FreeBSD has a few different flavours.
At the time of writing you can download these versions:

  - 13.0-RELEASE
  - 12.3-RELEASE
  - 13.1-RC2
  - 14.0-CURRENT
  - 12.3-STABLE

Below is an excerpt from the FreeBSD manual, <a href="https://docs.freebsd.org/en/books/handbook/cutting-edge/#current-stable" target="_new">section 24.5.1</a>:

> FreeBSD-CURRENT is the "bleeding edge" of FreeBSD development and FreeBSD-CURRENT users are expected to have a high degree of technical skill.
> Less technical users who wish to track a development branch should track FreeBSD-STABLE instead.

The RC2 version is the second release candidate for the new 13.1-RELEASE which will soon be available.
I have no need for the bleeding edge so I will stick to the 12.3-RELEASE which I will upgrade to 13.0-RELEASE.

FreeBSD presents a similar option to OpenBSD for the installation image: there is an image for a USB flash drive (memstick) or CD/DVD (bootonly, disc1, dvd1).
The difference lies in the amount of packages available on the installation medium.
I will take the middle ground and pick the disc1 image.

## Installing NetBSD

# Upgrading the BSDs

## Upgrading OpenBSD

## Upgrading FreeBSd

## Upgrading NetBSD
