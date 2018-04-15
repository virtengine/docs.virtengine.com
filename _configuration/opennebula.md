Opennebula Configuiration instructions

# Setup Front-End OpenNebula:

https://docs.opennebula.org/5.4/deployment/opennebula_installation/frontend_installation.html# 

## Follow instructions to install OpenNebula-Node + Master
~~~bash

wget -q -O- https://downloads.opennebula.org/repo/repo.key | apt-key add -

echo "deb https://downloads.opennebula.org/repo/5.4/Ubuntu/16.04 stable opennebula" > /etc/apt/sources.list.d/opennebula.list


sudo apt-get update
sudo apt-get install -y opennebula opennebula-sunstone opennebula-gate opennebula-flow
/usr/share/one/install_gems

cat /var/lib/one/.one/one_auth
oneadmin:password

# Back to root & start opennebula
systemctl start opennebula
systemctl start opennebula-sunstone

# Setup Compute OpenNebula (Can be run in the same node)

https://docs.opennebula.org/5.4/deployment/node_installation/index.html

sudo apt-get install opennebula-node
sudo service libvirt-bin restart #  ubuntu

sudo su oneadmin
cd ~/.ssh
cp id_rsa.pub authorized_keys
ssh oneadmin@localhost 
exit -> goes to oneadmin 
exit -> goes to root

#Test OpenNebula deployment 

oneuser show 
~~~

#Login to OpenNebula Admin Area

http://SERVER_IP:9869


# Configuire OpenNebula to work with VirtEngine

~~~bash
mkdir /virtengine

cd /virtengine

wget https://virtenginepub.blob.core.windows.net/gulpd/init.sh

chmod 755 /virtengine/init.sh

# Modify init.sh so that it can connect to VirtEngine API's (you can find settings around the bottom)
#  under [meta]
#  vertice_api = # Change to VirtEngine API Location: port 9000
#  nsqd = # Change to VirtEngine NSQD Location: port 4150
#  everything below these settings is updated in the VM Automatically in Deployment.
#  such as api key, account id, assembly id, and hostname.

nano /etc/one/oned.conf 
~~~

~~~conf
Ctrl + _ (Line 771)

VM_HOOK = [
 name      = "poweroff_hook",
 on        = "CUSTOM",
 state     = "ACTIVE",
 lcm_state = "SHUTDOWN_POWEROFF",
 command   = "hook_virtengine.rb",
 arguments = "$ID $TEMPLATE poweroff stopped" ]

VM_HOOK = [
 name      = "delete_hook",
 on        = "DONE",
 command   = "hook_virtengine.rb",
 arguments = "$ID $TEMPLATE destroyed destroyed" ]

VM_HOOK = [
 name      = "suspend_hook",
 on        = "CUSTOM",
 state     = "SUSPENDED",
 lcm_state = "LCM_INIT",
 command   = "hook_virtengine.rb",
 arguments = "$ID $TEMPLATE suspended suspended" ]

VM_HOOK = [
 name      = "boot_suspend_hook",
 on        = "CUSTOM",
 state     = "BOOT_SUSPENDED",
 lcm_state = "RUNNING",
 command   = "hook_virtengine.rb",
 arguments = "$ID $TEMPLATE running running" ]

VM_HOOK = [
 name      = "running_hook",
 on        = "CUSTOM",
 state     = "ACTIVE",
 lcm_state = "RUNNING",
 command   = "hook_virtengine.rb",
 arguments = "$ID $TEMPLATE running running" ]
~~~

~~~bash
wget https://raw.githubusercontent.com/VirtEngine/gitpackager/master/support/hook_virtengine.rb

cp hook_virtengine.rb /var/lib/one/remotes/hooks

chmod 755 /var/lib/one/remotes/hooks/hook_virtengine.rb

chown oneadmin:oneadmin /var/lib/one/remotes/hooks/hook_virtengine.rb

Create master_key in /var/lib/detio/:

#### If you want to modify the master key, you must modify the gateway configuiration file and set your own master key (recommended in production) - /var/lib/detio/virtenginegateway/gateway.conf 

cat >/var/lib/detio/master_key << EOF
host=http://YOUR_IP:9000/v2
masterkey=3b8eb672aa7c8db82e5d34a0744740b20ed59e1f6814cfb63364040b0994ee3f
EOF


cd /var/tmp

wget https://virtenginepub.blob.core.windows.net/iso/centos.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/coreos_latest.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/debian.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/dockermachine.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/fedora.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/ubuntu_16.04.tar.gz

wget https://virtenginepub.blob.core.windows.net/iso/ubuntu14.tar.gz

tar -zxvf ubuntu_16.04.tar.gz

tar -zxvf centos.tar.gz 

# centos_7.2.img

tar -zxvf ubuntu14.tar.gz

tar -zxvf coreos_latest.tar.gz
# coreos_latest

tar -zxvf debian.tar.gz 
# debian_8.5.img

tar -zxvf dockermachine.tar.gz 
# dockermachine.img

tar -zxvf fedora.tar.gz 
# fedora_24.img
~~~

The untar them individually and add them to the opennebula datastore with the following slugs (titles)

osname_version

for examples, ubuntu_14.04, windows_2008, centos_7.2, centos_6.8

add image named 'megam' with either ubuntu 16.04 OS or Centos, this will be used for deploying apps.

https://github.com/VirtEngine/gitpackager/tree/master/support


### Setup network bridge from eth0 -> br0
### Add network to OpenNebula
### Add images to OpenNebula
### Add VM Template to OpenNebula

#Add empty template first, update the template with the following settings. 
~~~yaml
CONTEXT = [
  FILES = "/virtengine/init.sh",
  NETWORK = "YES",
  NODE_NAME = "$NAME",
  SET_HOSTNAME = "$NAME",
  SSH_PUBLIC_KEY = "$USER[SSH_PUBLIC_KEY]" ]
CPU = "0.5"
CPU_COST = "0.022222"
DESCRIPTION = "common template for all images"
DISK = [
  IMAGE = "megam",
  IMAGE_UNAME = "oneadmin" ]
DISK_COST = "0.0044444"
GRAPHICS = [
  LISTEN = "0.0.0.0",
  TYPE = "VNC" ]
LABELS = ""
MEMORY = "1024"
MEMORY_COST = "0.011111"
NIC = [
  NETWORK = "public-1",
  NETWORK_UNAME = "oneadmin" ]
NIC_DEFAULT = [
  MODEL = "virtio" ]
OS = [
  ARCH = "x86_64" ]
SCHED_REQUIREMENTS = "CLUSTER_ID=\"100\""
VCPU = "1"
~~~
