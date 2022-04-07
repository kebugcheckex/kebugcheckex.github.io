---
title: Turn off screen in Linux using command line
layout: post
tags:
- linux
category: linux
---

This article explains how to turn off screen in Linux using command line.

<!--more-->

## In TTY mode

If you have physical access to the machine, run the following command
```
$ setterm --blank 1
```
This will turn off the screen after 1 minute wihout activity.

If you only have remote access to the machine (e.g. through SSH), you can do the following
```
$ setterm -term linux -blank < /dev/tty1
```
where `tty1` should be replaced by the actual tty you want to turn off. Use `who` command to figure out which tty is the one that is attached to the monitor.

## In GUI mode
_To be continued..._

## Reference
* https://askubuntu.com/questions/62858/turn-off-monitor-using-command-line
