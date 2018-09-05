---
title: OpenStack Hybrid Cloud
order: 2
---

This page explains more about what OpenStack is and how it fits in with VirtEngine.

---

## [VirtEngine](https://virtengine.com)

VirtEngine is an Open Source Hybrid Cloud Management platform that integrates with multiple infrastructure endpoints, one of them being OpenStack.

VirtEngine offers a Hosting Provider edition that provides the ability to offer Infrastructure to end-users with billing enabled.


## [OpenStack](http://openstack.org/)

OpenStack is an open source software that allows for the deployment and management of a cloud  infrastructure as a service (IaaS) platform. OpenStack supports both private and public cloud deployments. It fulfills two main requirements of the cloud: massive scalability and simplicity of implementation.

#### [Hypervisor Virtualization](https://wiki.openstack.org/wiki/HypervisorSupportMatrix)
- Group A:
- [KVM/QEMU](https://wiki.openstack.org/wiki/HypervisorSupportMatrix#Group_A)
- [Group B:
- [Hyper-V](http://wiki.cloudbase.it/hyperv-tempest-exclusions)
- [VMWare](https://wiki.openstack.org/wiki/NovaVMware/Minesweeper)
- [XenServer](https://wiki.openstack.org/wiki/XenServer/XenServer_CI)
- [Xen via libvirt](https://wiki.openstack.org/wiki/Xen/Libvirt)
- [Group C](https://wiki.openstack.org/wiki/HypervisorSupportMatrix#Group_C):
- [Bare-Metal](https://wiki.openstack.org/wiki/HypervisorSupportMatrix#Group_C)
- Docker Containers
- LXC via Libvirt

#### [Storage](https://docs.openstack.org/arch-design/design-storage/design-storage-concepts.html)
- Ceph
- Gluster
- LVM
- NFS
- iSCSI - Libvirt Datastore
- ZFS
- Sheepdog

#### [Networking](https://docs.openstack.org/arch-design/design-networking/design-networking-concepts.html)
- Bridged Networks
- 802.1Q VLAN Network
- VXLAN Networks
- Open vSwitch Networks

## Setup and Deployment

OpenStack can be deployed through various methods, the simplest being DevStack - however it would not be recommended to use DevStack for production and is instead a better tool for testing the platform. Other examples of deployments can be found here: [OpenStack Deployment](https://docs.openstack.org/queens/deploy/)

In order to use OpenStack with VirtEngine, you would need to install VirtEngine Waldur - Documentation can be found in [Waldur Documentation](http://docs.waldur.com)

