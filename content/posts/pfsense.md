---
author: "Justin Owens"
date: 2020-05-29
title: "pfSense Notes"
---


## MTU on LAGG
If you have a LAGG to pfSense then chances are this is your trunk with all your vlans.  Often there may be a situation when one of those vlan interfaces needs to have upgraded MTU size.  Unlike other standalone interfaces, any LAGG members cannot change their MTU in the interfaces assignment area.

Several posts from a few years back suggest it was a pretty big issue for awhile.  Some suggest to manually assign the LAGG an interface and change the MTU there.  DO NOT do this; you will bring down the network.  Atleast on version 2.4.5 and newer the below command is what you need.

`ifconfig lagg0 mtu 9000`

A reboot when possible would be ideal.

