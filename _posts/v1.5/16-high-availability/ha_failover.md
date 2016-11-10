---
title: Failover
type: enterprise
tags: "1.5"
---
#Securing uptime

###Minified Edition
The minified edition is powered by LVM storage, this does not provide any high availability what so ever.

##High Availability in Complete Edition
VirtEngine Storage is powered by Ceph, a massively scalable, open-source, software-defined storage solution developed from the ground-up to provide object, block and file system storage in one self-managing, self-healing platform. Using a high-reliability, non-stop architecture, Ceph is the ideal solution for powering a secure and next-generation cloud solutions.


#What is High Availability?

![VirtEngine High Availability for Hosting Providers](/images/layersofha.png "VirtEngine Sell Cloud Servers High Availability")

*  The VMs that run in the host are automatically moved to another Host. The storage of the VMs are redundant and abide by the principles. We store one extra copy that can reside in any of the other hosts OSD.
