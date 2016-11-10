---
title: "Php"
order: 4
excerpt: ""
---

You will enter VirtEngine's console white-labelled for you.

> UI [http://virtengine-master:8080](https://cloud.det.io:8080)  

Replace `virtengine-master` with the IP address of 

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

> [verticeapps/php_wordpress](https://github.com/verticeapps/php_wordpress.git)

> [verticeapps/php_fengoffice](https://github.com/verticeapps/php_fengoffice.git)

> [verticeapps/php_webanalytics](https://github.com/verticeapps/php_webanalytics.git)


### I have a Github id.

 Select your Github repository with source code.

### Adding a start script

The start script file of your php repository will be used to start the script from home directory.


##4. Step3

- Select the SSH Key options.

 You can create a new sshkey

 Use an existing sshkey or upload your own sshkeys too.


##5. Launch Php App

Click Launch.

##6. Make changes to your Php App code *optional*

Let us say we want to make changes in the code. In our case the sample starter pack app code [verticeapps/php_wordpress](https://github.com/verticeapps/php_wordpress.git)

Make sure you have the build tools like **git**, **maven**, or **gradle** installed

```
 cd java_springwebflow

 mvn install

```

##7. Push your changes *optional*

Let us say we are done testing the changes and want to push the changes to Github

```shell
cd java_springwebflow

git push master
Username for 'https://github.com': detio
Password for 'https://detio@github.com':
To https://github.com/detio/php_springwebflow
1d26d24..5cabacb  master -> master

```

Voila ! Your App is up to date.

Now that you have launched your app, you might want to launch a service (database) and bind it.
