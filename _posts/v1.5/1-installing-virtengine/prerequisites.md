---
title: Pre-requisites
order: 1
---

We assume that you have a working [OpenNebula](https://opennebula.org){: target="_blank"}. If not, we are here to bring you in our grooves by asking for help in our [forum](http://forums.virtengine.com){: target="_blank"}.

You can setup OpenNebula backed by [ceph](http://ceph.com){: target="_blank"} or [lvm](https://wiki.ubuntu.com/Lvm){: target="_blank"} to store images.
{: .info}

---

### Configuring OpenNebula

[VirtEngine](/) provides a marketplace for one click launches.  We need a running [OpenNebula](http://opennebula.org){: target="_blank"} with templates and images.


## Init script

The system gets booted by OpenNebula using the context `init.sh` for the purpose of setting up networking and agent inside the VM.

Hence a context shell script in directory */VirtEngine* should be created initially. For guidance please read  the documentation [provided here](https://github.comvirtenginesys/gitpackager/blob/master/support/README.md){: target="_blank"}.


## Import Images in OpenNebula

Import all the images in OpenNebula to your `datastore`.

To do this, download  and untar the images as per the instructions given below:

~~~bash


$ wget https://virtenginepub.blob.core.windows.net/iso/centos.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/coreos_latest.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/debian.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/dockermachine.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/fedora.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/ubuntu_16.04.tar.gz

$ wget https://virtenginepub.blob.core.windows.net/iso/ubuntu14.tar.gz


$ tar -zxvf ubuntu_16.04.img.tar.gz ubuntu_16.04.img

$ tar -zxvf coreos_latest.img.tar.gz

$ tar -zxvf ubuntu_14.04.img.tar.gz
mv ubuntu14.img ubuntu_14.04.img

$ tar -zxvf fedora_24.img.tar.gz
mv fedora.img fedora_24.img

$ tar -zxvf debian_8.5.img.tar.gz
mv debian.img debian_8.5.img

$ tar -zxvf centos_7.1.img.tar.gz
mv centos.img centos_7.1.img

$ tar -zxvf dockermachine.1.12.img.tar.gz
mv dockermachine.img dockermachine.1.12.img

~~~

Next, install VirtEngine to deploy virtual machines using OpenNebula [here](/1-installing-virtengine/installing).
{: .info}
