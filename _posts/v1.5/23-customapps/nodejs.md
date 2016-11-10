---
title: "Node.js"
excerpt: "Now, read further to get a clear walk through on how to deploy a Node.js app"
---

You will enter VirtEngine's console white-labelled for you.

> UI [http://detio:8080](https://detio)  

Replace `detio` with `your_ip`

Type the URL to launch apps, service and machines in a jiffy.

##1. Click Marketplaces or NEW

There are two ways to launch.

    a. Marketplace contains all the linux distros, applications, services and microservices.
    b. NEW

##2. Step1

Select region, HDD or SSD, flavor.

Click Next.

##3. Step2

### Public Repository

If you don't have an id, then type this `Public repository` in the text box.

> [verticeapps/node_etherpad](https://github.com/verticeapps/node_etherpad.git)

> [verticeapps/travis-web](https://github.com/verticeapps/travis-web.git)

> [verticeapps/ghost](https://github.com/verticeapps/ghost.git)


### I have a Github id.

 Select your Github repository with source code.

### Adding a start script.

The start script is used to automate install platform dependency in your application and then used to start your application.

The start scripts are built-in to the sample public repository.


##4. Step3

- Select the SSH Key options.

 You can create a new sshkey

 Use an existing sshkey or upload your own sshkeys too.


##5. Launch Node App

Click Launch.

##6. Make changes to your Node App code *optional*

Let us say we want to make changes in the code. In our case the sample starter pack app code [verticeapps/etherpad-lite](https://github.com/verticeapps/etherpad-lite.git)

Make sure you have the build tools like **git**, **npm** installed

```
 cd etherpad-lite

 npm install

```

##7. Push your changes *optional*

Let us say we are done testing the changes and want to push the changes to Github

```shell
cd etherpad-lite

git push master
Username for 'https://github.com': detio
Password for 'https://detio@github.com':
To https://github.com/oja/etherpad-lite.git
1d26d24..5cabacb  master -> master

```

Voila ! Your App is up to date.

Now that you have launched your app, you might want to launch a service (database) and bind it.
