

#### CentOS 7.2 *NOT SUPPORTED ATM*!

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
baseurl=https://get.virtengine.com/repo/1.5.2/centos/7.2/stable
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
