---
title: "Docker Machine"
excerpt: "Yeah, you can try accessing your containers securely via DockerMachine"
---

You will enter VirtEngine's console white-labelled for you.

> UI [http://detio:8080](https://detio)  

Replace `detio` with `your_ip`

Type the URL to launch apps, service and machines in a jiffy.

##1. Click Marketplaces or NEW

There are two ways to launch.

    a. Marketplace contains all the linux distros, applications, services and microservices.

##2. Step1

Select region, flavor, HDD or SSD.

##2. Step2

Select the "docker machine" image that you want to launch

##3. Step3

- Select the SSH Key options.

 You can create a new sshkey

 Use an existing sshkey or upload your own sshkeys too.


##4. Launch your DockerMachine

Click Launch.

Voila ! Your "Machine with Docker engine" is launched.

Now that you have launched,  you might want to install `docker-machine` and launch containers into it.

##4. Launch containers

[Install Docker Machine in your laptop](https://docs.docker.com/machine/install-machine/)

```
docker-machine create --url=tcp://<your_ip> custombox

$ docker-machine ls
NAME        ACTIVE   DRIVER    STATE     URL
custombox   *…

```
