---
title: Installing VirtEngine
order: 1
---

{% include install_bulb.md %}

At the start, install OpenJDK8 and cassandra for which the following are needed.

### Supported Platforms

| Operating System                        | Status                                                |
|:-------------------------------------- :| :---------------------------------------------------- |
| Ubuntu 14.04, 16.04, Debian 8.5         | Well tested                                           |

---

##### Ruby2.3

~~~bash

$ sudo apt-add-repository ppa:brightbox/ruby-ng

$ sudo apt-get -y update

$ sudo apt-get -y install ruby2.3 ruby2.3-dev

~~~

##### OpenJDK-8 (Cassandra DB Dependancy)

~~~bash

$ sudo apt-get install openjdk-8-jre-headless

~~~  
#### Cassandra 3.9

Install cassandra 3.9 by following the link for your operating system.


| Operating System             | Link                                                                                        |
|:--------------------------- :| :------------------------------------------------------------------------------------------ |
| Ubuntu 14.04/16.04/Debian 8.5|[Ubuntu/Debian](http://docs.datastax.com/en/cassandra/3.x/cassandra/install/installDeb.html){: target="_blank"} |
| Using tarball                |[All Linux using tarball](http://docs.datastax.com/en/cassandra/3.x/cassandra/install/installTarball.html){: target="_blank"}                                    |

##### Ubuntu 16.04

In case you find issues in installing cassandra 3.9 in *Ubuntu 16.04*, follow the instructions given below:

~~~bash

$ echo "deb http://www.apache.org/dist/cassandra/debian 39x main" | sudo tee -a /etc/apt/sources.list.d/cassandra.sources.list

$ curl https://www.apache.org/dist/cassandra/KEYS | sudo apt-key add -

$ sudo apt-get update

$ sudo apt-get install cassandra

~~~

### Install OpenSource VirtEngine

#### Ubuntu 14.04

~~~bash

  sudo apt-add-repository "deb [arch=amd64] http://get.virtengine.com/repo/1.5.2/ubuntu/14.04/stable trusty stable"

  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611

  sudo apt-get update

  sudo apt-get --allow-unauthenticated install virtenginenilavu virtenginegateway nsqd virtengine virtenginevnc

~~~

To start VirtEngine then

~~~bash

  sudo start nsqd

  sudo start nsqadmin

  sudo start nsqlookupd

  sudo start virtenginegateway

  sudo start virtenginevnc

  sudo start virtengine

  sudo sv start nginx

  sudo sv start unicorn

~~~

To stop VirtEngine then

~~~bash

  sudo stop nsqd

  sudo stop nsqadmin

  sudo stop nsqlookupd

  sudo stop virtenginegateway

  sudo stop virtenginevnc

  sudo stop virtengine

  sudo sv stop nginx

  sudo sv stop unicorn

~~~

#### Ubuntu 16.04/Debian Jessie

~~~bash

  sudo apt-add-repository "deb [arch=amd64] https://get.virtengine.com/repo/1.5.2/ubuntu/16.04/stable xenial stable"

  //sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611

  sudo apt-get update

  sudo apt-get --allow-unauthenticated install virtenginenilavu virtenginegateway nsqd virtengine virtenginevnc

~~~

To start VirtEngine

~~~bash

  sudo systemctl start nsqd

  sudo systemctl start nsqadmin

  sudo systemctl start nsqlookupd

  sudo systemctl start virtenginegateway

  sudo systemctl start virtenginevnc

  sudo systemctl start virtengine

  sudo sv start nginx

  sudo sv start unicorn

~~~

To stop VirtEngine

~~~bash

  sudo systemctl stop nsqd

  sudo systemctl stop nsqadmin

  sudo systemctl stop nsqlookupd

  sudo systemctl stop virtenginegateway

  sudo systemctl stop virtenginevnc

  sudo systemctl stop virtengine

  sudo sv stop nginx

  sudo sv stop unicorn

~~~


#### CentOS 7.2 *experimental*

At the start, install Ruby2.3 and Runit for VerticeNilavu.

##### Ruby2.3

~~~bash

$ wget https://github.com/feedforce/ruby-rpm/releases/download/2.3.1/ruby-2.3.1-1.el7.centos.x86_64.rpm

$ sudo yum install -y libyaml

$ sudo rpm -ivh ruby-2.3.1-1.el7.centos.x86_64.rpm

~~~
##### Runit

~~~bash

$ curl -s https://packagecloud.io/install/repositories/imeyer/runit/script.rpm.sh | sudo bash

$ sudo yum install -y runit-2.1.1-7.el7.centos.x86_64

~~~

~~~bash

  cat << EOT > /etc/yum.repos.d/virtengine.repo
[virtengine]
name=virtengine
baseurl=https://get.virtengine.com/repo/1.5/centos/7.2/stable
enabled=1
gpgcheck=0
EOT

  sudo yum update

  sudo yum install virtenginenilavu virtenginegateway nsqd virtengine virtenginevnc

~~~

To start VirtEngine

~~~bash

  sudo systemctl start nsqd

  sudo systemctl start nsqadmin

  sudo systemctl start nsqlookupd

  sudo systemctl start virtenginegateway

  sudo systemctl start virtenginevnc

  sudo systemctl start virtengine

  if sv service does not start to run the following command

  runsvdir /var/service &

  then do this

  sudo sv start nginx

  sudo sv start unicorn

~~~

To stop VirtEngine

~~~bash

  sudo systemctl stop nsqd

  sudo systemctl stop nsqadmin

  sudo systemctl stop nsqlookupd

  sudo systemctl stop virtenginegateway

  sudo systemctl stop virtenginevnc

  sudo systemctl stop virtengine

  sudo sv stop nginx

  sudo sv stop unicorn

~~~

### Docker Images

Here you may be in a position to use [Docker container for VirtEngine in Dockerhub](https://github.com/virtengine/docker_virtengine){: target="_blank"}