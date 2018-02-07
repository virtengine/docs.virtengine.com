---
title: OpenNebula + VirtEngine
order: 2
---

This page explains more about what OpenNebula is and how it fits in with VirtEngine.

---

## [OpenNebula](https://opennebula.org)

OpenNebula is a fully Open Source Management Platform that allows you to delpoy a Private Cloud to manage internally, OpenNebula has public API's which can allow third party software to interact with it which is how VirtEngine connects to OpenNebula to create and manage VM's.

#### [Virtualization](https://docs.opennebula.org/5.4/deployment/open_cloud_host_setup/index.html)
- [KVM](https://docs.opennebula.org/5.4/deployment/open_cloud_host_setup/kvm_driver.html)
- [VMWare vCenter](https://docs.opennebula.org/5.4/deployment/vmware_infrastructure_setup/index.html)
- [Xen (Supports 5.0)](https://github.com/OpenNebula/addon-xen)
- [LXC/LXD](https://github.com/OpenNebula/addon-lxcone)

#### [Storage](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/overview.html#datastore-types)
- [Filesystem](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/fs_ds.html#fs-ds)
- [Ceph](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/ceph_ds.html#ceph-ds)
- [LVM](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/lvm_drivers.html#lvm-drivers)
- [Raw Device Mapping Datastore](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/dev_ds.html#dev-ds)
- [iSCSI - Libvirt Datastore](https://docs.opennebula.org/5.4/deployment/open_cloud_storage_setup/iscsi_ds.html#iscsi-ds)

#### [Networking](https://docs.opennebula.org/5.4/deployment/open_cloud_networking_setup/index.html)
- [Bridged Networks](https://docs.opennebula.org/5.4/deployment/open_cloud_networking_setup/bridged.html)
- [802.1Q VLAN Networks](https://docs.opennebula.org/5.4/deployment/open_cloud_networking_setup/bridged.html)
- [VXLAN Networks](https://docs.opennebula.org/5.4/deployment/open_cloud_networking_setup/vxlan.html)
- [Open vSwitch Networks](https://docs.opennebula.org/5.4/deployment/open_cloud_networking_setup/vxlan.html)

## Setup and Deployment

OpenNebula is fairly simple to install and delpoy, and we recommend deploying it before installing VirtEngine.

VirtEngine is tested and stable with KVM, the default Hypervisor of OpenNebula.

In order to use Opennebula, you need to install Sunstone on a Management Server - and then install as much KVM Nodes as you'd like.

#### OpenNebula Front-End
Installing OpenNebula's Front-End includes the following packages:
- Sunstone (User Interface)
- CLI Tools
- Ruby API
- OpenNebula Daemon


#### [Front-End Deployment](https://docs.opennebula.org/5.4/deployment/opennebula_installation/index.html)


### OpenNebula KVM Node

When installing a KVM Node you must provide password-less access from the Master to the Node.

#### [KVM Node Deployment](https://docs.opennebula.org/5.4/deployment/node_installation/kvm_node_installation.html)


### Demo of Installing OpenNebula + VirtEngine

(Video Coming Soon)

### Demo of using OpenNebula + VirtEngine

(Video Coming Soon)