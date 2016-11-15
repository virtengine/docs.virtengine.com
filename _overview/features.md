---
title: Features
order: 4
permalink: /features
---

## High Availability

![VirtEngine High Availability for Hosting Providers](/images/ha.png "High Availability")

Achieving high availability is 'expensive' - well only for the traditional way of doing things, here at VirtEngine - you no longer have to shell out your precious money for expensive Storage Area Network setups and costly staff in order to achieve redundancy.

High Availability at VirtEngine works by storing a secondary copy of the Virtual Machines through a Network Raid 1 style system on available cloud storage. This can be achieved with two different setups:

### One Link High Availability
#### Minimal Setup

|                                  | Storage          | Network                                                                                                                                                                                                                                                  | Description                                                                                                                                                                                                                                                               |  |
| -------------------------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |  |
| Compute & Storage Node #1 (CSN1) | 2xHDD (or) 2xSSD | 1GBps Private Network                                                                                                                                                                                                                                    | One Drive is used for Storage, while the other is used for Compute (Virtual Machines). In this case, the storage drive will store all of CSN2's data.                                                                                                                     |  |
| Compute & Storage Node #2 (CSN2) | 2xHDD (or) 2xSSD | 1GBps Private Network                                                                                                                                                                                                                                    | The same thing applies here, the storage drive will store all of CSN1's data.                                                                                                                                                                                             |  |
| Failover Node #1                 | 1xHDD (or) 1xSSD | 1GBps Private Network                                                                                                                                                                                                                                    | This server is on stand by, generally for a large setup you will need more backup nodes however 1 for every 10 Compute Nodes is ideal. <br><br>This server is triggered when a node fails, for example if CSN1 fails - it will grab CSN1's data from CSN2 storage drives. |  |


For additional redundancy, you can also setup double copy - meaning that two copies of each compute node will be stored instead. This means that you will need to double your storage capacity.

### SAN Model 
#### Minimal Setup

|                         | Storage          | Network                                                                                                                                                                                                                                                  | Description                                                                                                                                                                                                                                                        |  |
| ----------------------- | ---------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |  |
| Compute Node #1 (CN1)   | 1xHDD (or) 1xSSD | 1GBps Private Network                                                                                                                                                                                                                                    | All the drives are usable by Virtual Machines, a copy is stored in SN1 for disasters.                                                                                                                                                                              |  |
| Storage Node #1 (SN1)   | 2xHDD (or) 2xSSD | 10GBps Private Network - Since multiple Compute Server nodes will be uploading their data to this SS1.                                                                                                                                                   | This storage server will store as much copies as it can from multiple Compute Server nodes. <br>Multiple Storage Servers can be added to form a cluster. <br>Compute Server nodes with storage enabled will also join the cluster.                                 |  |
| Failover Node #1        | 1xHDD (or) 1xSSD | 1GBps Private Network                                                                                                                                                                                                                                    | This server is on stand by, if CS1 fails - then it will grab the backups directly from SS1 and reboot all the virtual machines automatically.                                                                                                                      |  |

## Storage
### Object Storage

While Storage nodes are used for High Availability, they are also used for Object Storage. Clients can store data directly through an API into your cloud. Object Storage can be used for any data type, such as images, videos, or virtually any file extension.

#### Redundant

Object storage is also setup in a redundant way, multiple copies of your clients data will be stored. This can be setup to also support a multi-geographical setup for increased redundancy.

### Block Storage

Block Storage allows users to expand their VM Datastores, they can also be used to transfer large amounts of data from one server to another with minimal bandwidth usage by de-attaching the Block Storage and re-attaching it to a secondary Virtual Machine. 

Block Storage allows for safe scaling, as it is a seperate partition from the OS Partition - they can be removed at a later stage without affecting the server.

## Snapshots

Virtual Machines states can be snapshotted, this can be used as either a form of Backup that can be reverted to in a later stage - or a way to scale their compute demand by redeploying the snapshot. 
Users snapshots are automatically stored into the Object Storage system, and are billed accordingly. Users can snapshot a VM, delete the VM and then relaunch the Snapshot when they require it again.

## Application Deployments (PaaS)

### Custom Applications

Developed an Application in NodeJS, PHP, Ruby or a dozen other supported languages? Our PaaS system knows exactly how to deploy your application. All directly from your
GitHub repository, you can also enable Continous Integration and update the application automatically with every code push.

Now that's agility.

### Services

Launch Databases, Load Balancers, Analatics, Enterprise tools all in a click in order to enhance your application.

### One-Click Applications

VirtEngine supports the ability to launch & scale the following in a few clicks:

* 100k+ Docker Hub Applications - _Containers_
* 100's of the most Popular OpenSource Applications from Bitnami - _Virtual Machines_
* 100's of custom images maintained by VirtEngine.
* Add your own custom images with ease.
* Custom Applications from public GitHub repositories or private GitHub repostiories through linked accounts.

### Containers

Docker containers are awesome, but you don't see Infrastructure-as-a-Service providers offering them, we're changing that - your users can easily launch from 100's of thousands of docker images in 3 easy steps, search - select - click.

###Hyperscaling Applications
####Coming Soon

Applications launched through our PaaS system, support hyperscaling. Virtual Machines can be added to serve your application with a click, automatically load balanced and configuired through our system. Since our PaaS system knows exactly
how to deploy the application - it can clone the main server, deploy the application, add it to the load balancer all automatically.

This also works with services attached to the application, such as databases. When multiple databases are necessary, they are automatically clustered. 

####Multi-GEO scaling

If you support multiple locations, your users can now achieve absolute redundancy by deploying a copy of the server over multiple locations. Thus, even if one of your locations have had a fatal disruption - the application is still reachable
through loadbalancing. Even load balancers can be setup this way so that even if one of the load balancers are disrupted, another takes over.

Now a CDN network to serve applications is possible with ease thanks to VirtEngine's innovative features.

##Ease of Deployment
###Automation

Hosting providers, especially reasonable sized ones - have a lot of hardware. Launching a cloud with tons of hardware can get complicated quickly, let alone managing and scaling it. 

It shouldn't take days to launch a cloud platform, and weeks to configure it. Anyone whose tried to launch an OpenStack cloud knows the struggle. We solve this with our automated cloud launcher. Making the decision will take longer than getting on-boarded, don't waste valuable time and resources, start selling immediately. 

### Virtual Private Cloud

Want to offer your clients all the above features, but they prefer private clouds? You can provision your infrastructure with our software directly for them.

## Billing (Public Cloud)

### Native WHMCS support

We support WHMCS off the bat, because we know that WHMCS is the GOTO Billing System for Hosting Providers. This means that you can still sell all the other services that are
supported by WHMCS without an issue. 

Customers can redirect from the WHMCS application -> VirtEngine Dash and back to -> WHMCS with just a click. Our pre-built themes also make it look like they haven't left the
cloud platform at all to avoid confusion.

### On-Demand Billing (Hourly)

Customers can add credit directly onto their WHMCS accounts through any of WHMCS's supported payment gateways. Once credit is available, clients can launch instances
from Virtual Machines to Applications. Credit is then removed on an hourly bases, Virtual Machines are suspended once a set threshold is passed. For example, if you'd like
to suspend machines automatically once credit reaches $0.00 - that's possible. It can even be a negative number like $-10.00 to avoid frustration.

### Quota Based Plans (Monthly/Yearly)

If clients know that they will always be using resources, then plans are the way to go - since they can be set to be cheaper than hourly fees. Plans will allow users to create
resources up to a set limit of their plan. Once they reach that limit they can upgrade their plans for additional resources.

# Summary 
* Unpack, configure your hardware to Cloud in seconds. 

* High Availability made affordable and easy.

* Storage Solutions.

* Full featured PaaS with replication, scalability, CI, and support for containers.

* Host your compute nodes wherever you please. 

* Supports multi-geolocation setups. 

* Native WHMCS billing support.

