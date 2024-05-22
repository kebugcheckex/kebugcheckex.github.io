---
title: Useful Linux Tips
layout: post
tags:
  - linux
category: linux
---

This article contains various Linux tips. I will add more content from time to time. If this article grows too large, I may split it into several different articles with some categorization.

<!--more-->

## Turn on/off USB port power during sleep

Use kernel parameter `usbcore.autosuspend=-1`. Set this in `/etc/default/grub`. Append the parameter in `GRUB_CMDLINE_LINUX_DEFAULT`.

## Mount ISO files

```console
# mount -o loop /path/to/iso/file.iso /media/iso
# umount /media/iso
```

## Install RPM packages on Arch Linux

Install `rpmextract` package and run `rpmextract.sh package-name.rpm`. Then install the generated package using `pacman -U`. More complicated situation use `alien` tool (need more research on this).

## GNU make options

- `make -n -s -d` shows the detailed command of each build step

## IP command

- Turn on/off interface `sudo ip link set <interface> up/down`

## Zip related

- Set compress level `zip -0 <archive_name>.zip <file_or_directory>`
- Verify integrity `zip -T your-archive.zip` or `tar -Wf archive.tar`

## Pipe View

Use `pv` to show zip or tar progress

```console
$ zip -r -0 -q - * | pv -lep -s $(du -sb | awk '{print $1}') > archive.zip
$ tar cf - . | pv -lep -s $(du -sb | awk '{print $1}') | gzip > archive.tar.gz
```

## WiFi related

```console
# rfkill unblock <device>
```

## Xpra

- Server side: `xpra start :DISPLAY_NUMBER --start-child=COMMAND`
- Client side: `xpra attach ssh:USER@REMOTE_HOSTNAME:DISPLAY_NUMBER`

Use high number for display, e.g. 100

## GNOME

- Start GNOME control center (Settings) from command line `gnome-control-center`

## KDE

- Install KDE on Ubuntu `sudo apt install kde-plasma-desktop` (full packages) or `sudo apt install kde-standard` (smaller installation)
- Network Manager config UI: `plasma-nm`
