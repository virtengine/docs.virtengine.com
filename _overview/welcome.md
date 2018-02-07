---
title: Welcome
order: 1
permalink: /
---

### Homepage

[VirtEngine - Powering Public & Private Clouds](http://virtengine.com)


## What is VirtEngine?

VirtEngine is an excellent turnkey Virtualization platform that enables businesses to build, run scale and manage virtual machines, apps, containers entirely in your own fault tolerant cloud.

VirtEngine supports both a public model (for hosting providers) & a private model (for internal use)

VirtEngine works by integrating with OpenNebula, Docker, and Ceph to offer VM / Containers & Storage to the end-user.

### What is a cloud?

A Cloud is a group of Phsyical Computing resources that provides flexibily to the users, users are able to launch Computing Power on demand.

### What defines a cloud?

A '**Cloud**' is generally a reference to '**Cloud Computing**' which is a form of computing that can be utilized to serve applications, websites, databases, and much more.

Cloud Computing comes with a few Essential Characteristics in order to be recognized as 'cloud' instead of just Virtual Private Servers.

These essential characteristics, as defined by the **US Government** include:

- **On-demand self-service :**
The user can access, delete instances, or add new instances on-demand as required.

Hourly Billing allows the above to be possible, where-as monthly billing strips that on-demand availability away since you can no longer downscale when required (must wait till the month is over).

- **Broad network access :**
Able to access the service remotely.

- **Resource pooling :**
Virtual resources dynamically assigned and reassigned according to consumer demand. A multi-tenant model where multiple users can utilize this resource pool is required.

- **Rapid elasticity :**
Capabilities can be elastically provisioned and released, in some cases automatically. There must always be idle computing power ready to be used by the consumer - and scaled on demand by the provider, the user must not wait for resources.

- **Measured service :**
Monitoring & Transparency of usage is a requirement, the user must be able to monitor required services such as Bandwidth, Storage, etc.

- **High Availability (optional):**
Clouds are generally considered to be hardware agnostic, meaning that the virtual machines don't specificly rely on the hardware they are running on. 
This means that when a Physical Server fails due to hardware failure, misconfiguiration, or simply power outages - then the Virtual Machines within the hardware that has failed can migrate automatically
onto a new host with no data loss and minimal service interruption. 

Cloud Computing also comes with Service Models such as -

- **Infrastructure-as-a-Service**
For all other service models, they rely on an Infrastructure endpoint. Infrastructure as a Service is what powers the Virtual Machines in order to have access to Computing Power, storage, a network, and more.
- **Platform as a Service** & **Software as a Service**
Which are designed to save time and automate processes that are previously manual. Such as deploying custom applications, pre-packaged applications, databases, load balancers, etc .
- **Storage as a Service**
Cloud Storage includes things such as Block Storage (Extending your Virtual Machines storage), Snapshotting VM's (to re-launch or recover at a later stage), Redundancy (storing data multiple times) & Object Storage (the ability to store data into a resource pool through an API or VirtEngine's UI).

### What is the difference between Private & Public cloud?

A private cloud is a pool of resources that only the owner and permitted users are able to access the resources, the owner may have full control over the hardware the cloud is running on (By Collocating his hardware at a Datacenter) or may 
lease dedicated servers from a Hosting Provider. 

A public cloud on the other hand is a pool of resources that is available to the public, in return the user pays for the resources he utilizes on an hourly bases.

## What VirtEngine offers

VirtEngine provides management & orchestration of a small to large number of Virtual Machines, Containers, Applications, Storage Solutions and other Cloud Services.  When those machines are no longer required they are "released" back into the resource pool. VirtEngine integrates all the tools you require in one smooth experience. It includes:

- A beautiful & UX based web UI
- Full API support
- High availability (optional)
- IPv6 support
- Open Cloud Platform
- Virtual Machines (Templates)
- Custom Applications (Platform as a Service)
- Docker Containers
- Install Applications in Virtual Machines (100+ through Bitnami)
- Billing Integrated for Hosting Providers
- VirtEngine works with any form of Physical Hosts and comes with Minimal Requirements to setup.

### Getting Started

Getting your private platform as service is easy with VirtEngine:

#### Installation Methods
1. OpenSource, requires an existing OpenNebula installation - Limited to Private Cloud Community Edition
2. Through our Onboard Cloud SaaS offering, which will launch everything automatically in your own servers. - Licensed and Includes all VirtEngine featuers

1. At the outset, know the [System requirements](/gettingstarted/system_requirements/)
2. Understand the prerequisities for your [installation](/installation/prequisites/)
3. [Install](/installation/VirtEngine/)
4. [Configure VirtEngine](/configuration/VirtEngine)
5. Deploy a [Virtual Machine](/machines/deploying/) or [Application](/customapps/deploying)

Follow the [Tour](/overview/tour/) to explore the available and forth coming features.
{: .info}

---

### Features

Get the most from VirtEngine by following the documentation for each feature:

#### {% include icons/backup.svg %} Virtual Machines
{: id="file-syncing"}

[Deploy](machines/deploying) your favourite virtual machine of any flavor (Core, RAM, HDD) of any kind such as Ubuntu, CentOS, Debian, CoreOS, DockerMachine and Windows or even from your own snapshots.

#### {% include icons/edit.svg %} 100's of Bitnami apps in a second
{: id="editing"}

Fast search and launch of more than 100 prebuilt [bitnami apps](/prepackagedapps/deploying/). We also provide our images for popular apps like WordPress, OwnCloud, Discourse etc.

#### {% include icons/public.svg %} 1000's of Docker registry using intuitive search
{: id="hosting"}

VirtEngine has [fast intuitive search](containers/deploying) built in, to nail the container you wish to launch. The search skims the public docker registry and reports as many results  as it finds.

#### {% include icons/dns.svg %} Customapps
{: id="domains"}

Enabled to launch [Custom App](/customapps/deploying/) from a public git url or Github from your own repository for launguages like Java, Node.js, Php, Rails, C/C++, Python.

#### {% include icons/people.svg %} Multi region  Data center
{: id="sharing"}

Made easy for customers to deploy in multi regions(eg: Sydney, Germany) if you have your datacenter located in two different location in the same city or different countries.

#### {% include icons/settings.svg %} Billing Integration WHMCS
{: id="advanced"}
Embedded with WHMCS for dynamic billing to your customers for server resource usage like disk space, RAM or CPU usage for a periodic interval.

Contact us at [hello@virtengine.com](mailto:hello@virtengine.com) with any questions or feedback.
{: .info}
