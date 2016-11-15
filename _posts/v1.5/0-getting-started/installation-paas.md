---
title: "Installing"
excerpt: "Get set go to bootstrap your own open source PaaS"
---
Before we begin, lets install OpenJDK8 and cassandra.

##OpenJDK8

###Ubuntu 14.04
[block:code]
{
  "codes": [
    {
      "code": "sudo apt-add-repository -y ppa:openjdk-r/ppa\n\nsudo apt-get -y update\n\nsudo apt-get -y install openjdk-8-jdk",
      "language": "shell",
      "name": "trusty - openjdk8"
    }
  ]
}
[/block]
###Ubuntu 16.04
[block:code]
{
  "codes": [
    {
      "code": "sudo apt-get install openjdk-8-jre-headless",
      "language": "shell",
      "name": "xenial - openjdk8"
    }
  ]
}
[/block]
###Debian Jessie
[block:code]
{
  "codes": [
    {
      "code": "echo \"deb http://http.debian.net/debian jessie-backports main\" > /etc/apt/sources.list\n\nsudo apt-get update\n\nsudo apt-get install openjdk-8-jre-headless\n\nsudo apt-get install openjdk-8-jdk\n\nsudo /usr/sbin/update-java-alternatives -s java-1.8.0-openjdk-amd64",
      "language": "shell",
      "name": "jessie - openjdk8"
    }
  ]
}
[/block]
###CentOS 7.0
[block:code]
{
  "codes": [
    {
      "code": "su -c \"yum install java-1.8.0-openjdk\"",
      "language": "shell",
      "name": "centos7 - openjdk8"
    }
  ]
}
[/block]
##Cassandra 3.x 

[Ubuntu/Debian](http://docs.datastax.com/en/cassandra/3.x/cassandra/install/installDeb.html)
[CentOS](http://docs.datastax.com/en/cassandra/3.x/cassandra/install/installRHEL.html)
[All Linux using tarball](http://docs.datastax.com/en/cassandra/3.x/cassandra/install/installTarball.html)

###Install PaaS - VirtEngine

##Ubuntu 14.04
[block:code]
{
  "codes": [
    {
      "code": "sudo apt-add-repository \"deb [arch=amd64] http://get.virtengine.com/repo/1.5/ubuntu/14.04/stable trusty stable\"\n\n\nsudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611\n\nsudo apt-get update\n\nsudo apt-get install VirtEnginenilavu VirtEnginegateway VirtEnginensq VirtEngine VirtEnginevnc",
      "language": "shell",
      "name": "Ubuntu"
    }
  ]
}
[/block]
##Ubuntu 16.04/Debian Jessie

Use the jessie packages for Ubuntu 16.04
[block:code]
{
  "codes": [
    {
      "code": "sudo apt-add-repository \"deb [arch=amd64] http://get.virtengine.com/repo/1.5/debian/8.5/testing jessie testing\"\n\nsudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 9B46B611\n\nsudo apt-get update\n\nsudo apt-get install VirtEnginenilavu VirtEnginegateway VirtEnginensq VirtEngine VirtEnginevnc",
      "language": "shell",
      "name": "Jessie/xenial"
    }
  ]
}
[/block]
##CentOS 7.0
[block:code]
{
  "codes": [
    {
      "code": "sudo yum update\n\nsudo yum install VirtEnginenilavu VirtEnginegateway VirtEnginensq VirtEngine VirtEnginevnc",
      "language": "shell"
    }
  ]
}
[/block]
##Docker Images

Habitat (Docker images) are [coming thru](https://github.com/megamsys/habitat_plans).
[block:html]
{
  "html": "<div></div>\n<a class=\"megam-button\" href=\"megam_megdc_tool\" role=\"button\">One step to finish, configuration</a>\n<style>\n\n</style>"
}
[/block]