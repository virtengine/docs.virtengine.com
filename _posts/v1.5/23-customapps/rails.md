---
title: "Ruby on Rails"
excerpt: "Now, read further to get a clear walk through on how to deploy a Rails app"
---
You will enter Megam VirtEngine [UI http://localhost:8080](doc:VirtEngine_up)  through which you can launch apps, service and machines, monitor them seamlessly.

##1. Click Marketplaces on the top bar  or `NEW`

Marketplace contains all the linux distros,  applications, services and microservices which VirtEngine supports. 

##3. Click Rails icon (Ruby)

A window will pop up with for SSHkey options. You can create new sshkey, use an existing sshkey or upload your own sshkeys too. 

##4. Configure SSHKeys

You're almost there

##5. Pick a repository 

Choose your public or private repository. Let us use [Github: virtengine/VirtEngine-UI](https://github.com/virtengine/VirtEngine-UI.git)

##6. Launch Rails App

Click Create.

##7. Make changes to your Rails App code *optional*

Let us say we want to make changes in the code. In our case the sample starter pack app code is [Github: virtengine/VirtEngine-UI](https://github.com/virtengine/VirtEngine-UI.git)
[block:code]
{
  "codes": [
    {
      "code": "$ git clone https://github.comvirtenginesys/nilavu.git",
      "language": "shell"
    }
  ]
}
[/block]
Make sure you have the build tools like **rvm**, **bundler**, **gem** installed with my favourite editor [atom](http://atom.io)
[block:code]
{
  "codes": [
    {
      "code": "$ cd nilavu\n\n$ bundle update\n\n$ bundle install",
      "language": "shell"
    }
  ]
}
[/block]
##8. Push your changes *optional*

Let us say we are done testing the changes and want to push the changes to Git/Github
[block:code]
{
  "codes": [
    {
      "code": "$ cd nilavu\n\n$ git push master\n\nUsername for 'https://github.com': megamio\nPassword for 'https:/virtengineio@github.com': \n\nTo https://github.com/indykish/nilavu.git\n   1d26d24..5cabacb  master -> master\n",
      "language": "shell"
    }
  ]
}
[/block]
Voila ! Your App is up to date.


Now that you have launched your app, you might want to launch a service (database) and [bind it](doc:megam_bind_app)

[block:html]
{
  "html": "<div></div>\n<a class=\"megam-button blue\" href=\"postgresql\" role=\"button\">Go to the services</a>\n<style>\n\n</style>"
}
[/block]

[block:callout]
{
  "type": "info",
  "body": "[Support - Gitter room/info@virtengine.com](doc:contact-us)",
  "title": "Any questions? We're always here to help"
}
[/block]