---
title: Kubernetes Hybrid Cloud
order: 2
---

This page explains more about what Kubernetes is and how it fits in with VirtEngine.

---

## [VirtEngine](https://virtengine.com)

VirtEngine is an Open Source Hybrid Cloud Management platform that integrates with multiple infrastructure endpoints, one of them being Kubernetes.

VirtEngine achieves this by integrating with Rancher for the automated deployment of Kubernetes Clusters: Secure, Multi-Cluster Kubernetes Everywhere


## [Kubernetes](https://kubernetes.io)

Kubernetes, also known as K8s, is an open-source system for automating deployment, scaling, and management of containerized applications.

### Editions Supported
- [Rancher Clustering](https://rancher.com)
- [Kubernetes Distributions](https://kubernetes.io)
- [OpenStack](https://openstack.org)

#### [Supported Concepts](https://kubernetes.io/docs/concepts/)
- [Containers](https://kubernetes.io/docs/concepts/containers/)
- [Workloads](https://kubernetes.io/docs/concepts/workloads/)
- [Load Balancing](https://kubernetes.io/docs/concepts/services-networking/)
- [Storage](https://docs.opennebula.org/5.6/deployment/open_cloud_storage_setup/ceph_ds.html#ceph-ds)
- [Security & Configuration](https://kubernetes.io/docs/concepts/security/)
- [Networking](https://docs.opennebula.org/5.6/deployment/open_cloud_storage_setup/lvm_drivers.html#lvm-drivers)


## Setup and Deployment

Rancher is fairly simple to install and delpoy, we recommend having a direct OpenStack deployment as the system utilizes openstack to power cluster deployments.

VirtEngine is tested and stable with KVM, the default Hypervisor of OpenStack.

In order to use OpenStack, you need to follow the documentation found here: [OpenStack Deployment](https://docs.openstack.org/2024.1/deploy/index.html)

To deploy VirtEngine Waldur, follow the documentation found here: [Waldur Documentation](https://docs.waldur.com)
