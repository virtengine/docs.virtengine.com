---
title: "General"
excerpt: "There are caveats to look at when cofiguring Vertice."
---
#Lets configure your open source PaaS - Vertice

By default no configuration change is required if everything runs in a single server.

Tweaks are needed to supporting VPS, Containers.

##UI

1. */var/lib/megam/site_settings.yaml* file is self explanatory, tweak as you wish.

2. */var/lib/megam/nilavu.conf*
[block:code]
{
  "codes": [
    {
      "code": "## api host that the UI will connect to\nhttp_api = localhost\n\n## log stream that the UI will connect to. \nlog_server = ws://localhost:7777/logs\n\n### vnc server that the UI will connec to.\nvnc_server = ws://localhost:8000",
      "language": "text",
      "name": "/var/lib/megam/nilavu.conf"
    }
  ]
}
[/block]
##API

1. */var/lib/megam/verticegateway/gateway.conf*
[block:code]
{
  "codes": [
    {
      "code": "# Cassandra instance\n# ~~~~~\nscylla.host = \"localhost\"\nscylla.keyspace = \"vertice\"\nscylla.username = \"megam\"\nscylla.password = \"pass\"\n\n\n# NSQ messaging daemon\n# ~~~~~\nnsq.url=\"http://localhost:4151\"\nnsq.topic.vms=\"vms\"\nnsq.topic.containers=\"containers\"\n\n#Domain name that your instances will run.\n# ~~~~~\ndomain = \"megambox.com\"",
      "language": "text",
      "name": "/var/lib/megam/verticegateway/gateway.conf"
    }
  ]
}
[/block]
##Scheduler (Vertice)

1. */var/lib/megam/vertice/vertice.conf*
[block:code]
{
  "codes": [
    {
      "code": "\n  ### Controls how vertice connects to scylla, nsq\n  [meta]\n    api = \"http://localhost:9000/v2\"\n    nsqd = [\"localhost:4150\"]\n    scylla = [\"192.168.0.116\"]\n    scylla_keyspace = \"vertice\"\n\n  ###\n  ### [deployd]\n  ###\n  ### Controls how the deployer endpoints are configured. These are the primary \n  ### mechanism for VPS. The default option is to support opennebula.\n  \n  ### Here we configure a region named `chennai` with 2 clusters.\n\n  [deployd]\n    provider = \"one\"\n\n      [deployd.one]\n        enabled = true\n        vcpu_percentage = \"3\"\n\n          [[deployd.one.region]]\n            one_zone = \"chennai\"\n            one_endpoint = \"http://localhost:2633/RPC2\"\n            one_user     = \"oneadmin\"\n            one_password = \"onepass\"\n            one_template = \"megam\"\n\n              [[deployd.one.region.cluster]]\n                enabled = true\n                cluster_id = \"101\"\n                vnet_pri_ipv4   = \"pri_ipv4\"\n                vnet_pub_ipv4   = \"pub2_ipv4\"\n                vnet_pri_ipv6   = \"pri_ipv6\"\n                vnet_pub_ipv6   = \"pub_ipv6\"\n\n\n              [[deployd.one.region.cluster]]\n                enabled = true\n                cluster_id = \"100\"\n                vnet_pri_ipv4   = \"pri_ipv4-a\"\n                vnet_pub_ipv4   = \"pub_ipv4-a\"\n                vnet_pri_ipv6   = \"pri_ipv6-a\"\n                vnet_pub_ipv6   = \"pub_ipv6-a\"\n\n\n\n  ###\n  ### [http]\n  ###\n  ### A mini webserver for pinging vertice to tell us the status\n  ###\n\n  [http]\n    enabled = true\n    bind_address = \"localhost:7777\"\n\n  ###\n  ### [docker]\n  ###\n  ### controls one or many listeners for docker\n  ###\n\n   [docker]\n    provider = \"docker\"\n\n      [docker.docker]\n          enabled = true\n          [[docker.docker.region]]\n            docker_zone = \"chennai\"\n            swarm = \"tcp://192.168.0.121:2375\"\n\n\n\n          [[docker.docker.region]]\n            docker_zone = \"sydney\"\n            swarm = \"tcp://localhost:2375\"\n\n\n\n  ###\n  ### [dns]\n  ###\n  ### Controls how the dns endpoints are configured.\n  ### The default dns supported is AWS - Route53. You need to have account.\n  ###\n\n  [dns]\n    enabled = true\n    access_key = \"abcd\"\n    secret_key = \"efgh\"\n\n  ###\n  ### Controls how the system metrics collection needs to be configured.\n\n  [metrics]\n    enabled = false\n    collect_interval = \"10m\"\n\n  ###\n  ### Controls how the events needs to be configured and handled by watchers\n\n  [events]\n    enabled = true\n\n    [events.mailgun]\n      api_key = \"temp\"\n      domain  = \"ojamail.megambox.com\"\n      nilavu = \"https://console.virtengine.com\"\n      logo = \"https://s3-ap-southeast-1.amazonaws.com/megampub/images/mailers/megam_vertice.png\"\n\n    [events.infobip]\n      username = \"info_username\"\n      password = \"info_pw\"\n      api_key  = \"info_apiky\"\n      application_id = \"info_apiid\"\n      message_id = \"info_msgid\"\n\n    [events.slack]\n      token = \"temp\"\n      channel = \"ahoy\"\n\n    [events.bill]\n      piggybanks = [\"scylladb\",\"whmcs\"]\n      whmcs_key = \"dummykey\"\n      whmcs_username = \"\"\n      whmcs_password = \"\"\n      whmcs_domain = \"http://localhost.com/billing\"",
      "language": "text",
      "name": "/var/lib/megam/vertice/vertice.conf"
    }
  ]
}
[/block]

[block:html]
{
  "html": "<div></div>\n<a class=\"megam-button\" href=\"http://docs.virtengine.com/docs/debian\" role=\"button\">Go to launch a machine</a><style></style>"
}
[/block]