---
title: Node.js
order: 3
---

These steps are in continiuation from step2 in the section [deploying](/customapps/deploying).

---

## Step2 continued...

There are 2 ways to launch.

1. *Using a Public Repo URL*
2. *I have a Github account*

### Using a Public Repo URL

If you don't have an id, then type these `Public repo url` in the text box.

[https://github.com/VirtEngineapps/node_etherpad](https://github.com/VirtEngineapps/node_etherpad.git){: target="_blank"}

[https://github.com/VirtEngineapps/travis-web](https://github.com/VirtEngineapps/travis-web.git){: target="_blank"}

[https://github.com/VirtEngineapps/ghost](https://github.com/VirtEngineapps/ghost.git){: target="_blank"}


### I have a Github id.

Choose your Github repository.

### Adding a build script. *optional*

The *build script* is used to install additional build steps in the launched application that is deemed fit for your launched app.

For your convenience the sample public repos has baked in build scripts as needed.

The build script needs to be named as *build* and shall reside under the parent root directory.

Now that you have chosen the git repo, [Go to step3 to launch](/customapps/deploying).

### Adding a start script. *optional*

The *start script* is used to install additional start steps in the launched application that is deemed fit for your launched app.

For your convenience the sample public repos has baked in build scripts as needed.

The build script needs to be named as *build* and shall reside under the parent root directory.

Now that you have chosen the git repo, [Go to step3 to launch](/customapps/deploying).


### Working with Node App code *optional*

To make changes in the code [VirtEngineapps/etherpad-lite](https://github.com/VirtEngineapps/etherpad-lite.git){: target="_blank"} ensure that you have the build tools like **git**, **npm**, and **node** installed.

```

 cd etherpad-lite

 npm install

```

### Push your changes to Github *optional*

Once you are done testing the changes, push the changes to Github.


```shell

cd etherpad-lite

git push master
Username for 'https://github.com': VirtEngineuser
Password for 'VirtEngineuser@github.com':
To https://github.com/VirtEngineapps/etherpad-lite.git
1d26d24..5cabacb  master -> master

```
