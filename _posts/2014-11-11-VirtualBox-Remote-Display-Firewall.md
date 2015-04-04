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
<img class="img-responsive" alt="VirtualBox Machine Display Settings for Remote Display"
     src="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxSettingsScreenshot-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxSettingsScreenshot-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/VirtualBoxSettingsScreenshot-min.jpg 657w"
     sizes="(min-width:768px) 657px,
            calc(100vw - 30px)" />

When I tried to use remote desktop from another machine on the same local network I was unable to connect.
My first thought was to enable the Remote Desktop rules already present within the Windows Firewall.<br />
<img class="img-responsive" alt="Windows 7 Firewall incoming rules for Remote Desktop"
     src="{{ site.baseurl }}/assets/2014-11-11/RemoteDesktopScreenshot-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/RemoteDesktopScreenshot-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/RemoteDesktopScreenshot-min.jpg 937w"
     sizes="(min-width:768px) 937px,
            calc(100vw - 30px)" />

However this also resulted in a connection error.
To resolve the issue I had to allow VirtualBox to accept incomming connections.<br />
<img class="img-responsive" alt="Windows 7 Firewall incoming rules for VirtualBox"
     src="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxScreenshot-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/VirtualBoxScreenshot-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/VirtualBoxScreenshot-min.jpg 937w"
     sizes="(min-width:768px) 937px,
            calc(100vw - 30px)" />

To create this rule, under Inbound Rules select New Rule and choose Program as the rule type.<br />
<img class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 1"
     src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-1-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-1-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-1-min.jpg 728w"
     sizes="(min-width:768px) 728px,
            calc(100vw - 30px)" />

Next, find the location of the VirtualBox executable, for me it was C:\Program Files\Oracle\VirtualBox\VirtualBox.exe<br />
<img class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 2"
     src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-2-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-2-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-2-min.jpg 728w"
     sizes="(min-width:768px) 728px,
            calc(100vw - 30px)" />

Next, choose to allow the connection.<br />
<img class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 3"
     src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-3-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-3-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-3-min.jpg 728w"
     sizes="(min-width:768px) 728px,
            calc(100vw - 30px)" />

Next, I didn't want the rule to be applied to Public networks but I was OK with Pivate and Domain networks.<br />
<img class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 4"
     src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-4-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-4-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-4-min.jpg 728w"
     sizes="(min-width:768px) 728px,
            calc(100vw - 30px)" />

Finally, you can choose to give the rule a name and description.<br />
<img class="img-responsive" alt="Windows 7 Firewall New Incoming Rule Step 5"
     src="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-5-small-min.jpg"
     srcset="{{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-5-small-min.jpg 260w,
             {{ site.baseurl }}/assets/2014-11-11/Firewall-Add-App-Rule-Step-5-min.jpg 728w"
     sizes="(min-width:768px) 728px,
            calc(100vw - 30px)" />

After that I was able to connect from the secondary machine.

Tools I used:

- Windows 7 Firewall
- [VirtualBox 4.3.12](https://www.virtualbox.org/)