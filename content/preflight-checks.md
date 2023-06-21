+++
title = "Preflight Checks"
description = "Or how to make sure you're on the right network"
date = 2023-06-19
slug = "preflight"
draft = false
+++

It's been a while, and I wanted to get back to my metasploitable series but have decided instead to document a robust methodology for penetration testing. This is by no means suppost to be *the* way to do things, but it's my own personal method documented (and hopefully updated, future Halfwhit!) for reference.

So, why do a preflight check?
Well, have you ever fired up Kali and connect to a network only to start, or even finish, a nice chunky nmap scan only to find you were'nt connected? Well this is what the preflight check is for. There are tools we can use to check if we are connected to the network we intended to connect to, all of which will be checked off begining any engagement as a sanity check.

One of the simplist ways to check you have a connection, is through the GUI. This is great for a quick glance at what is going on, but I much prefer to use the command line to get my bearings within a network; One of the most widely known tools for checking connectivity is the mighty `ping` command.

Ping (pong!) is a great tool for checking if you can make a connection to the specified IP address, though not all hosts will respond to the ICMP ping packet sent. We will use ping at least twice, once to ping a host on the network (if the IP address is known) and again to ping an external DNS nameserver to check internet connectivity, for which I will use Google's (8.8.8.8).

If we have connected to a network with DHCP enabled, we are able to `cat /etc/resolve.conf` which will display the domain name and primary nameserver (DNS). This file is autopopulated by NetworkManager, but can also be changed manually.

