---
layout: post
title: 'Firewall settings for VirtualBox remote display'
date: '2014-11-11 19:00:00 -0700'
author: jaredhall05
categories: VirtualBox
---

This post is about how to configure the Windows 7 firewall to allow VirtualBox Remote Display.
I had a long running process running in a virtual machine that I wanted to monitor from another machine while I was working on other things.
I started by opening the settings for my virtual machine and navigating to Display->Remote Display and enabling the server.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxSettingsScreenshot.jpg" class="img-responsive" alt="VirtualBox Machine Display Settings for Remote Display" />

When I tried to use remote desktop from another machine on the same local network I was unable to connect.
My first thought was to enable the Remote Desktop rules already present within the Windows Firewall.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/RemoteDesktopScreenshot.jpg" class="img-responsive" alt="Windows 7 Firewall incoming rules for Remote Desktop" />

However this also resulted in a connection error.
To resolve the issue I had to allow VirtualBox to accept incomming connections.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxScreenshot.jpg" class="img-responsive" alt="Windows 7 Firewall incoming rules for VirtualBox" />

To create this rule, under Inbound Rules select New Rule and choose Program as the rule type.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-1.jpg" class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 1" />

Next, find the location of the VirtualBox executable, for me it was C:\Program Files\Oracle\VirtualBox\VirtualBox.exe<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-2.jpg" class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 2" />

Next, choose to allow the connection.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-3.jpg" class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 3" />

Next, I didn't want the rule to be applied to Public networks but I was OK with Pivate and Domain networks.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-4.jpg" class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 4" />

Finally, you can choose to give the rule a name and description.<br />
<img src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-5.jpg" class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 5" />

After that I was able to connect from the secondary machine.

Tools I used:

- Windows 7 Firewall
- [VirtualBox 4.3.12](https://www.virtualbox.org/)