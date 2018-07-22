---
title: VirtEngine
order: 1
requirements:
  build: VirtEngine
  plan: free
---

In order to faciliate to use our products the following informations are useful:

1. When you are using a single server for effecting all operations the  default configuration suffices.

2. When you are in a position to use separate servers to run VirtEngine or encounter failures while running, the following configurations are to be changed.

The following are the main components which are to be changed:

- *Console (UI - Nilavu)*
- *API - gateway*
- *Omni scheduler - VirtEngine*

### Changing components

The main options to change are in the following files:

1. Change details for the UI               */var/lib/detio/nilavu.conf*
*/etc/nginx/conf.d/nilavu.conf*
2. Change details for the API              */var/lib/detio/virtenginegateway/gateway.conf*
3. Change details for the Omni scheduler   */var/lib/detio/vertice/vertice.conf*

Go to

```bash

$ cd /var/lib/detio

```
Configure */etc/nginx/conf.d/nilavu.conf*
{: .info}

*/etc/nginx/conf.d/nilavu.conf*

~~~yaml

## nilavu UI that connect to

upstream nilavu {
  server localhost:8080;
}

~~~

Configure */var/lib/detio/nilavu.conf*
{: .info}

*/var/lib/detio/site_settings.yaml* file is self explanatory, tweak as you wish.

*/var/lib/detio/nilavu.conf*

~~~yaml

## api host that the UI will connect to

http_api = http://localhost:9000/v2

## log streamer that the UI will connect to.

log_server = ws://localhost:7777/logs

### vnc server that the UI will connect to.

vnc_server = ws://localhost:8000

~~~

Configure */var/lib/detio/virtenginegateway/gateway.conf*
{: .info}


~~~yaml

# We use  cassandra as the db layer
# ~~~~~

# Cassandra
# ~~~~~~~~~
cassandra.host = "localhost"
cassandra.keyspace = "VirtEngine"
# DON'T Change these
cassandra.username = "vertadmin"
cassandra.password = "vertadmin"
cassandra.use_ssl = false

~~~

~~~yaml

# We use NSQ as the messaging layer
# ~~~~~
nsq.url="http://localhost:4151"

# Don't change the nsq.topic names.
nsq.topic.vms="vms"
nsq.topic.containers="containers"

# send messages to NSQ.
nsq.events.muted = false

# don't send events to NSQ if the email id is tour@virtengine.com
nsq.events.muted_emails = ["tour@virtengine.com"]

~~~

Import *Vertice Keyspace in Cassandra*
{: .info}

## Update the keyspace in Cassandra

To do this, download  the following cql files:

~~~bash
wget https://raw.githubusercontent.com/VirtEngine/gateway/1.5.2/db/base.cql

wget https://raw.githubusercontent.com/VirtEngine/gateway/1.5.2/db/1.5.cql

wget https://raw.githubusercontent.com/VirtEngine/gateway/1.5.2/db/1.5.1.cql

wget https://raw.githubusercontent.com/VirtEngine/gateway/1.5.2/db/1.5.2.cql

wget https://raw.githubusercontent.com/VirtEngine/gateway/1.5.2/db/ee.cql


~~~

~~~bash
cqlsh -f base.cql

## Update base.cql file in cassandra. Change localhost to your private_ip
## Modify cassandra.yaml in /etc/cassandra/ -> authenticator: PasswordAuthenticator, authorizer -> CassandraAuthorizer

~~~

Enable *password-auth in cassandra*
{: .info}

Open the file */etc/cassandra/cassandra.yaml* in your favourite EDITOR.

Lets use *nano*

~~~bash

$ nano  /etc/cassandra/cassandra.yaml

~~~

- Change authenticator  “AllowAllAuthenticator” to “PasswordAuthenticator”.

- Change authorizer “AllowAllAuthorizer” to “CassandraAuthorizer”

~~~yaml

  # - AllowAllAuthenticator performs no checks - set it to disable authentication.
  # - PasswordAuthenticator relies on username/password pairs to authenticate
  #   users. It keeps usernames and hashed passwords in system_auth.credentials table.
  #   Please increase system_auth keyspace replication factor if you use this authenticator.
  #   If using PasswordAuthenticator, CassandraRoleManager must also be used (see below)
  authenticator: PasswordAuthenticator

  # - AllowAllAuthorizer allows any action to any user - set it to disable authorization.
  # - CassandraAuthorizer stores permissions in system_auth.permissions table. Please
  #   increase system_auth keyspace replication factor if you use this authorizer.
  authorizer: CassandraAuthorizer

~~~


Restart the cassandra (in all operating systems)

~~~bash

$ service cassandra restart

~~~

~~~bash

## Upgrade the cql file using cassandra username and password. change localhost to your private_ip

cqlsh -u vertadmin -p vertadmin -f 1.5.cql

cqlsh -u vertadmin -p vertadmin -f 1.5.1.cql

cqlsh -u vertadmin -p vertadmin -f 1.5.2.cql

cqlsh -u vertadmin -p vertadmin -f ee.cql

~~~

Configure */var/lib/detio/vertice/vertice.conf*
{: .info}


~~~yaml

### Welcome to the VirtEngine configuration file.
###
### [meta]
###
### Controls how VirtEngine connects to API (Gateway Project)

  [meta]
  api = "http://localhost:9000/v2"  #"https://api.megam.io/v2"
  master_user = "virtengine@det.io"
  master_key = "3b8eb672aa7c8db82e5d34a0744740b20ed59e1f6814cfb63364040b0994ee3f"
  nsqd = ["localhost:4150"]
    
~~~
