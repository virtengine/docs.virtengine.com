---
title: System Requirements
order: 1
---

In order to get the most out of a VirtEngine, we recommend you to create a plan with the following features:
  * Performance
  * Scalability
  * High availability

This guide provides comprehensive information in such a way that you can easily architect your deployment and utilize the technologies involved in the management of virtualized resources and their relationship.

# Architecture Overview

![System Architecture for VirtEngine](/images/architecture-overview.png){: srcset="/images/architecture-overview.png 800w, /images/architecture-overview.png 1600w"}
{: .has-screenshot}

We assume that your physical hardware supports Virtualization & adopts a classical cluster-like architecture with a front-end, which is the only specific system requirement. 

A set of hosts where Virtual Machines (VM)/Containers (Docker/OpenVZ) or unikernel will be executed within the hypervisors.

## Minimal: 

![VirtEngine Minimum System requirements for Public Cloud](/images/minimal.png "Minimum System Requirements for VirtEngine"){: srcset="/images/minimal.png 800w, /images/minimal.png"}
{: .has-screenshot}

| Application                     | Description                                                                                     | Quantity                     |
| ------------------------------- | ----------------------------------------------------------------------------------------------- | ---------------------------- |
| Master                          | Hosts our Software Stack, such as our provisioning engine and front-end etc.                    | 1                            |
| Compute Node - Virtual Machines | A compute node to host virtual machines                                                         | > 1                          |

Recommended:

| Application                     | Description                                                                                     | Quantity                       |
| ------------------------------- | ----------------------------------------------------------------------------------------------- | ------------------------------ |
| Master                          | Hosts our Software Stack, such as our provisioning engine and front-end etc.                    | 1                              |
| Slave                           | Slaves are additional nodes that host the VirtEngine software, they can be used to loadbalance the platofm or       | 1                              |
| Compute Node - Virtual Machines | A compute node to host virtual machines                                                         | > 1                            |
| Compute Node - Containers       | A compute node to host containers                                                               | > 1                            |
| Storage Node                    | A storage node to power High Availability & Storage Solutions                                   | > 1                            |
| Failover Node                   | A compute node that is on idle, it is utilized for high availability when a compute node fails. | > 1 for every 10 compute nodes |

## Typical setup:

You need at-least 2 servers to support compute, storage and containers. *Please refer topology section for more details.*

## Hardware Requirements

The basic requirements of structure and type of hardware(a) and operating system(b) for the effective use our product are:

a. Hardware

### 1. LVM

LVM and its volumes present the approach to build clusters using commodity hardware attached to compute nodes.

![Topology receommended](/img/gettingstarted/lvm-architecture.png){: srcset="/img/gettingstarted/lvm-architecture.png 800w, /img/gettingstarted/lvm-architecture.png 1600w"}
{: .has-screenshot}

Every compute node possesses its own LVM volume.
### 2. Ceph - High Availability

Achieving High Availability adds onto your system requirements, in order to support High Availability your storage will need to be setup in a specific way. And you need to support a strong private network 
in order to backup data on the go and retrieve them when required.

Minimal: 

* 2xHDD (or) 2xSSD per Compute Storage Node

or 

* 1xHDD (or) 1xSSD per Compute Node
* 2xHDD (or) 2xSSD Storage Node (SAN)

and

* 1GBps Private Network capacity.

Recommended:

* 1xSSD & 2xHDD (or) 3xSSD per Compute Node - Seperate the OS in an SSD Drive from the Virtual Machine storage

or

* 1xSSD & 1xHDD (or) 2xSSD per Compute Node
* 4xHDD (or) 4xSSD Storage Node (SAN)

and

* 10GBps Private Network capacity.

Just have a look at the tables below for the minimum & recommended hardware requirements.

### Standard Setup: 

Minimal Setup: 

|                      | CPU (Cores)   | RAM (GB)     | HDD                                |
| -------------------- | ------------- | ------------ | ---------------------------------- |
| Master (VM)          | 2/4           | 4-8GB        | 1xHDD (160GB) (or) 1xSSD (160GB)   |
| Slave (VM) (Optional ^1)           | 2/4           | 4-8GB        | 1xHDD (160GB) (or) 1xSSD (160GB)   |
| Compute/Storage Node | > 8/16        | > 16GB       | > 1xHDD (500GB) (or) 1xSSD (240GB) |
| Failover Node (Optional ^2)        | > 4/8         | > 16GB       | > 1xHDD (500GB) (or) 1xSSD (240GB) |

Recommended Setup: 

|                      | CPU (Cores)   | RAM (GB)     | HDD                                |
| -------------------- | ------------- | ------------ | ---------------------------------- |
| Master (VM)          | 8             | 16-32GB      | 1xSSD (240GB)                      |
| Slave (VM)           | 8             | 16-32GB      | 1xSSD (240GB)                      |
| Compute/Storage Node | > 8/16        | > 64GB       | > 3xHDD (2TB) (or) 3xSSD (750GB)     |
| Failover Node        | > 8/16        | > 64GB       | > 2xHDD (2TB) (or) 2xSSD (750GB)     |

^1: The purpose of a slave is to provide high availability for the VirtEngine UI & Software.
^2: The purpose of a failover node is to provide high availability to client VM's, for high availability to work please view the above requirements.

### SAN Setup:

![Topology SAN Like](/img/gettingstarted/san_architecture.png){: srcset="/img/gettingstarted/san_architecture.png 800w, /img/gettingstarted/san_architecture.png 1600w"}
{: .has-screenshot}


Minimal Setup (SAN): 

|               | CPU (Cores)   | RAM (GB)     | HDD                                |
| ------------- | ------------- | ------------ | ---------------------------------- |
| Master (VM)   | 2/4           | 4-8GB        | 1xHDD (160GB) (or) 1xSSD (160GB)   |
| Slave (VM)    | 2/4           | 4-8GB        | 1xHDD (160GB) (or) 1xSSD (160GB)   |
| Compute Node  | > 4/8         | > 16GB       | > 1xHDD (500GB) (or) 1xSSD (240GB) |
| Storage Node  | > 2/4         | > 8GB        | > 2xHDD (500GB) (or) 2xSSD (240GB) |
| Failover Node | > 4/8         | > 16GB       | > 1xHDD (500GB) (or) 1xSSD (240GB) |

Recommended Setup (SAN): 

|               | CPU (Cores)   | RAM (GB)     | HDD                                |
| ------------- | ------------- | ------------ | ---------------------------------- |
| Master (VM)   | 8             | 16-32GB      | 1xSSD (240GB)                      |
| Slave (VM)    | 8             | 16-32GB      | 1xSSD (240GB)                      |
| Compute Node  | > 8/16        | > 64GB       | > 2xHDD (2TB) (or) 2xSSD (1TB)     |
| Storage Node  | > 8           | > 16GB       | > 4xHDD (2TB) (or) 4xSSD (1TB)     |
| Failover Node | > 8/16        | > 64GB       | > 2xHDD (2TB) (or) 2xSSD (1TB)     |

b. Operating Systems

Ubuntu 14.04/16.04, Debian 8.5 and *experimental* for CentOS 7.2.

The compute/storage is scalable which means that  you can keep adding on. The storage can be a separate cluster as well.

The compute can be either VMs (KVM) or Containers(Docker/LXC).

Master is the server where VirtEngine is installed to manage the `compute` and `storage`.

Slave is the fallback node for the Master.

## Topology

The following depicts a 3 Node topology. Additional storage can done in master/slave itself.

The following section details the supported topology models using LVM and Ceph:

![Topology SAN Like](/img/gettingstarted/architecture_overview.png){: srcset="/img/gettingstarted/architecture_overview.png 800w, /img/gettingstarted/architecture_overview.png 1600w"}
