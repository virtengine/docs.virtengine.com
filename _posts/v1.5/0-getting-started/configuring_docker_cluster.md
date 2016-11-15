---
title: "Installing CaaS"
excerpt: "Optional, if you need containers then add it in here."
---
[block:api-header]
{
  "type": "basic",
  "title": "CaaS (Dockers on baremetal)"
}
[/block]
Here are the steps to enable containers support in opensource PaaS. 

We will use **docker 1.12** on bare metal.
[block:parameters]
{
  "data": {
    "h-0": "Prerequisites",
    "0-0": "You require atleast one <b>swarm master</b>    and lots of <b>node(s)</b> with Docker 1.12."
  },
  "cols": 1,
  "rows": 1
}
[/block]
#swarm

Let setup swarm master. A small server or VM is fine. 

## 1 Install swarm master
[block:code]
{
  "codes": [
    {
      "code": "curl -fsSL https://get.docker.com/ | sh\n\ndocker run --rm swarm create\n\nUnable to find image 'swarm:latest' locally\nlatest: Pulling from library/swarm\n220609e0bc51: Pull complete \nb54bf338fe2f: Pull complete \nd53aac5750d5: Pull complete \nDigest: sha256:c9e1b4d4e399946c0542accf30f9a73500d6b0b075e152ed1c792214d3509d70\nStatus: Downloaded newer image for swarm:latest\n\nb38992e6f59c094272e42dd92d72ace2  //this is your unique cluster id",
      "language": "shell",
      "name": "Pull the swarm from DockerHub."
    }
  ]
}
[/block]
Save the unique CLUSTERID which is **b38992e6f59c094272e42dd92d72ace2**
[block:code]
{
  "codes": [
    {
      "code": "docker run -t -p 2375:2375 -t swarm manage -H :2375 --addr <private/public hostip>:2375  token://b38992e6f59c094272e42dd92d72ace2",
      "language": "shell",
      "name": "Run swarm master in a private/public ip."
    }
  ]
}
[/block]
Now upon completion, swarm master is up and running.

## 2 Let us now prepare your node(s).

This has to be repeated in all the baremetal nodes. 
[block:code]
{
  "codes": [
    {
      "code": "curl -fsSL https://get.docker.com/ | sh\n\n//start the docker deaemon with defult subnet for docker0 bridge\n sudo docker daemon -D -H tcp://<private/public nodeip>:2375 --bip <subnet>/24 --default-gateway <ip>",
      "language": "shell"
    }
  ]
}
[/block]
Now the docker is up and running in the node using the **subnet**


## 3 Cluster all the nodes to the swarm master.

Use the CLUSTERID you got in **1.**

Now, join the  node to swarm master.

Paste the token and execute the below command on the master to join node to master
[block:code]
{
  "codes": [
    {
      "code": "docker run -d swarm join --advertise=<private/public nodeip>:2375 token://b38992e6f59c094272e42dd92d72ace2",
      "language": "shell"
    }
  ]
}
[/block]
See [VirtEngine configuration](doc:VirtEngine_configuration)  to enable support for container launches.

Voila! Go ahead and launch multiple docker containers through megam VirtEngine.