---
title: "Prerequisites"
excerpt: "Well, you need to tinker a little bit and setup one click images."
---
#Configuring OpenNebula

[Vertice](doc:megam_vertice_gettingstarted) provides a marketplace for one click launches.  We need a running [OpenNebula](https://opennebula.org) with a template and some images.

You are free to setup either [ceph](http://ceph.com) or [lvm](https://wiki.ubuntu.com/Lvm) to store images. Hopefully you have all the templates setup in OpenNebula.

##Vertice context script 
We will use a context `init.sh` script to setup stuff inside the VM/VPS from our PaaS.

So lets create a context shell script in the directory '/vertice`.  The script is as shown below.
[block:embed]
{
  "html": false,
  "url": "https://github.com/megamsys/libmegdc/blob/master/init.sh",
  "title": "megamsys/libmegdc",
  "favicon": "https://assets-cdn.github.com/favicon.ico"
}
[/block]

[block:code]
{
  "codes": [
    {
      "code": "mkdir /vertice\n\ncd vertice\n\nwget https://raw.githubusercontent.com/megamsys/libmegdc/master/init.sh\n\nls",
      "language": "shell",
      "name": "/vertice/init.sh"
    }
  ]
}
[/block]
Make sure you update the opennebula tempates with `FILES="/vertice/init.sh"`
[block:code]
{
  "codes": [
    {
      "code": "CONTEXT = [\n  FILES = \"/vertice/init.sh\",\n  NETWORK = \"YES\",\n  NODE_NAME = \"$NAME\",\n  SET_HOSTNAME = \"$NAME\",\n  SSH_PUBLIC_KEY = \"<COPY_PASTE_YOUR_SSH_PUBLIC_KEY>\" ]\nCPU = \"0.5\"\nCPU_COST = \"5\"\nDESCRIPTION = \"testing Xenial images\"\nDISK = [\n  IMAGE = \"megam\",\n  IMAGE_UNAME = \"oneadmin\" ]\nGRAPHICS = [\n  LISTEN = \"0.0.0.0\",\n  TYPE = \"VNC\" ]\nMEMORY = \"1024\"\nMEMORY_COST = \"10\"\nNIC = [\n  NETWORK = \"ipv4-pri\",\n  NETWORK_UNAME = \"oneadmin\" ]\nOS = [\n  ARCH = \"x86_64\" ]\nSCHED_REQUIREMENTS = \"CLUSTER_ID=\\\"100\\\"\"\nVCPU = \"1\"\nNAME=\"megam\"",
      "language": "text"
    }
  ]
}
[/block]
##Import Images in OpenNebula

The namings should be *centos_7.1* as it appears **centos_7.1.img** sans *img*
[block:code]
{
  "codes": [
    {
      "code": "wget https://s3-ap-southeast-1.amazonaws.com/megampub/iso/ubuntu_14.04.img.tar.gz\n\nwget https://s3-ap-southeast-1.amazonaws.com/megampub/iso/ubuntu_16.04.img.tar.gz\n\nwget https://s3-ap-southeast-1.amazonaws.com/megampub/iso/centos_7.1.img.tar.gz\n\nwget https://s3-ap-southeast-1.amazonaws.com/megampub/iso/debian_8.0.img.tar.gz\n\nwget https://s3-ap-southeast-1.amazonaws.com/megampub/iso/megam.img.tar.gz\n\ntar -zxvf ubuntu_14.04.img.tar.gz ubuntu_14.04.img\n\ntar -zxvf ubuntu_16.04.img.tar.gz ubuntu_16.04.img\n\ntar -zxvf debian_8.0.img.tar.gz debian_8.0.img\n\ntar -zxvf centos_7.1.img.tar.gz centos_7.1.img\n\ntar -zxvf coreos.img.tar.gz coreos.img\n\ntar -zxvf megam.img.tar.gz megam.img",
      "language": "shell",
      "name": "ubuntu_14.04"
    }
  ]
}
[/block]
 Import all the images in OpenNebula to your `datastore`.
[block:html]
{
  "html": "<div></div>\n<a class=\"megam-button\" href=\"vertice_configuration\" role=\"button\">Go to the configuring open source vertice.</a>\n<style>\n\n</style>"
}
[/block]