---
title: "Compiling"
excerpt: "So you have decided to extend and contribute"
---
#Source to your own open source PaaS - Vertice

[We have instructions in the Wiki](https://github.com/megamsys/vertice/wiki)

#Concepts

Feel free to read about the concepts. 

Vertice consists of applications, services, build packs, and other components.

##Applications

In Vertice, an application, or app, represents the artifact that a developer is building.

##Web apps

Web apps consist of all the code that is required to be run or referenced at run time. Web app artifacts are uploaded to  Vertice to host the application. 

##Services

A service is a cloud extension that is may be hosted by  Vertice  or created by you. The service provides functionality that is ready-for-use by the app’s running code. The predefined services provided by  include database, messaging, big data.

Vertice simplifies the use of services by provisioning new instances of the service, and binding those service instances to your application. 

##Runtimes

A runtime is the set of resources that is used to run an application. Vertice provides runtime environments for different types of applications. The runtime environments are integrated as buildpacks into Vertice, and are automatically configured for use.

##Buildpacks

A buildpack is a collection of scripts that prepare your code for execution on the target. A buildpack gathers the runtime and framework dependencies of an application. Then, it packages them with the application that can be deployed to the cloud.
If you do not specify a buildpack when you deploy your application to Vertice, built-in buildpacks are used by default.
[block:callout]
{
  "type": "info",
  "title": "Built-in Buildpacks",
  "body": "Java\nRuby\nNode.js"
}
[/block]
##Application Lifecycle

This describes the lifecycle of an app, from the time it is deployed through its removal. 

* User starts by going to the [etherpad-lite](https://github.com/verticeapps/etherpad-lite) on GitHub and cloning the Node.js application to a local notebook machine.

* User then makes changes and pushes the code in GitHub.

* User launches Vertice cockpit (Code named: [Nilavu](https://github.com/verticeapps/nilavu.git)) browser-based user interface and creates an application with the GitHub link.

* User then sees the application appearing in the Vertice  palette of applications launched

* User deletes an application when you are done with it

The app lifecycle is illustrated by the sequence diagram below.

The various states transitions an Application may undergo are shown below.

**State**
This illustration represents the transitions between app execution states. The next several sections of this topic describe these states and events.

Let us represent the application as *x*

`Launching`
When *x* is launching on the cloud (Iaas)

`Launched`
When *x* is launched on the cloud (Iaas) successfully

`Bootstrapping`
When *x*'s agent starts bootstrapping
- Agent will only run when you are in `launched` state
- Agent is a mini daemon that runs inside *x* if *x* is a vm. 

`Bootstrapped`
When *x*'s agent bootstrapped successfully

`Stateup`
When *x*'s agent is moving the state up

`Running`
When *x*'s agent stateup is successfull. This is where we should `trigger <x> is running email`

`Starting`
When *x*'s agent is starting the service
- Agent will only start when you are in `running, or ____ed [started, stopped, upgraded]` state

`Started`
When *x*'s agent has started the service

`Stopping`
When *x*'s agent is stopping the service
- Agent will only stop when you are in `running, or ____ed [started, stopped, upgraded]` state

`Stopped`
When *x*'s agent has stopped the service

`Upgraded`
When *x*'s agent has upgraded the operation
- Agent will only upgrade when you are in `running, or ____ed [started, stopped, upgraded]` state

For more information, read this [pull request](https://github.com/megamsys/gulp/pull/104)