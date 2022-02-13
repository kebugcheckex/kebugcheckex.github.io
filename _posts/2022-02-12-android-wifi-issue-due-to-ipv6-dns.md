---
title: Android WiFi Issue Due to IPv6 DNS
category: android
tags:
- android
- wifi
- networking
- ipv6
- dns
layout: post
---

Today my Google Pixel 6 suddenly hadissues with WiFi connection. The symptom is that it keeps disconnecting from WiFi, then reconnects, and after a few seconds, disconnects again. I didn't make any changes to the phone's network settings so initially I could not associate this issue with any recent changes. I tried to restart the phone, reset network configs, etc. None of them solved the issue. Logcat shows a few entries related to WiFi but not very useful for troubleshooting.

I use OpenWRT on my router. There are some custom configs, e.g. DHCP offers local DNS server over public DNS server, for my home networking usage. I realized that recently I added a local IPv6 DNS server address in the DHCP config so that all the connected device will resolve domain names to my local DNS server if they are using IPv6. This works fine until I rebooted my DNS server for regular maintenance. I didn't set static IPv6 address for my DNS server so the IPv6 address changed. After removing the IPv6 DNS from DHCP config, my Pixel 6 was able to connect to WiFi normally again.

Without digging into Android's source code, my theory is that Android tries to resolve some well-known domains (e.g. google.com) upon connecting to the WiFi network. If that fails, it will consider this network not usable and disconnects from it. Although this doesn't explain that why my other phones (e.g. Pixel 2 running Android 11, Xiaomi Mi 8 running Android 10) didn't have this issue. I don't know why Android at least try the IPv4 DNS server before disconnecting from WiFi.

Anyways, problem is solve. If you ever run into the same issue, try this solution.
