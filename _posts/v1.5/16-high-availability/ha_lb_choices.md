---
title: "Load Balancing(LB) in HA"
excerpt: "When we want to setup HA, we need to understand how LB works."
---
Lets take a closer look at what a Megdc HA deployment looks like.

#LB HA Topology

##HA with LB in Master node

Master node runs [HAProxy](http:\\haproxy.org), which manages a single External Virtual IP (VIP) for all front-end nodes and provides HTTP and TCP load balancing of requests going to [OpenNebula](http:\\docs.opennebula.org) & [Megam Oja](doc:megam_oja_gettingstarted). In this mode when the master fails then the requests will not go through the  [HAProxy](http:\\haproxy.org) which mean you need to access  [OpenNebula](http:\\docs.opennebula.org) & [Megam Oja](doc:megam_oja_gettingstarted) using the **Slave’s ip address**.

##HA with external LB external

An external node runs [HAProxy](http:\\haproxy.org), which manages a single External Virtual IP (VIP) for all front-end nodes and provides HTTP and TCP load balancing of requests going to  [OpenNebula](http:\\docs.opennebula.org) & [Megam Oja](doc:megam_oja_gettingstarted). In this mode as the [HAProxy](http:\\haproxy.org) is external to the Master and Slave, [HAProxy](http:\\haproxy.org) will continue to work on a failure to Master or Slave.
