# Provisioning like a Chef - Part 1
#### Configuring your workstation to talk with the Chef-Server.

![Chef icon](http://docs.opscode.com/_static/opscode_chef_html_logo.png)

## Overview

Every project needs, at least, one person that knows how to configure and install all components that make your infrastructure.

In the IT's vocabulary we call this person as **System Administrators** (SysAdmin). SysAdmins are the hardware's gods in your company, they work in the Operational Department and know how to configure and control your enviroment.

With the Startup buzz a new Role is shining, they are called **devops**.

DevOps is a developer with System Administration's competencies. They will setup your enviroment, not as sysadmin tunes, and you are ready to get traction/ make money.

With the DRY ( *Don't Reapeat Yourself* ) principle in mind, Chef was built. Chef is an automation framework that makes it easy to provisioning servers.

Using Chef, we create one **Cookbook** that will contains instructions ( **Recipes** ) to configure your machine ( **Node** ).

**Disclaimer**: IMHO, system administrators are really necessary to Tuning your enviroment/ perform audits routine/OS updates, patchs/ Networking infrastructure/ Security Holes and may others duties that is not the main skill for one developer.

## Goal

This MENU will guide you through 4 steps to enable your Workstation to talk with the Chef-Server.


## Chef components

##### Chef Server

Is the main repository for your **cookbooks**. Is the central piece that aggregate informations about all nodes in your network.

There are 3 flavors that you could use:

* Hosted Chef ( Chef as SaaS provided by Opscode)
* Private Chef ( Chef on the premises of the person. Inside your organization.)
* Open Source Chef Server ( Open Source Version that contains much of the same funcionality as Hosted Chef. All fixes, updates you must apply by yourself).


##### Node

A node is whatever host that have one **chef-client** installed.

The node will be provisioned with *recipes* that was configured in the **Chef-Server**.

When you command the provisioning, the **Node** will communicate with the **Chef-Server** using the configured **chef-client**. The chef-client contains the recipe execution environment that will run recipes that you configured in the chef-server for the specific node.

##### Workstation

The workstation is your playground ( Your development machine ). In the workstation you create the cookbooks and upload to the chef-server. 

The workstation talks with the chef-server using the *Knife* command line tool.

Knife is a command-line tool that provides an interface between a local Chef repository ( your workstation directory structure files ) and the Chef-Server. 


![chef Overview](http://docs.opscode.com/_images/overview_chef_draft.png) 


## 4 steps to reach the moon

### Step 1 
###### Creating your Hosted Chef account.

After this step, you will be able to see your organization configured in the [Management Area](http://manage.opscode.com)

1. Go to the [Opscode](http://www.opscode.com) site and Signup the service.
2. After Signup, go to [Management Area](http://manage.opscode.com)

### Step 2
###### Configuring your workstation
After this step you will have the conventional structure to your workstation. ( Convention over Configuration used by Knife)

This structure, convention over configuration, will enable you use knife without efforts.
for instance: "knife cookbook site install nginx" will install the nginx cookbook from the community site inside the cookbooks directory.

Clone the [Chef-Repo](https://github.com/opscode/chef-repo) from opscode github account.

````
 ~/chef $ git clone git://github.com/opscode/chef-repo.git
 ~/chef $ cd chef-repo
````

Create .chef directory.

.chef directory will contains the chef-server certificates used to authenticate the knife with the server/organization.

````
~/chef/chef-repo $
~/chef/chef-repo $ mkdir -p .chef
~/chef/chef-repo $ tree .

├── .chef
├── LICENSE
├── README.md
├── Rakefile
├── certificates
│   └── README.md
├── chefignore
├── config
│   └── rake.rb
├── cookbooks
│   └── README.md
├── data_bags
│   └── README.md
├── environments
│   └── README.md
└── roles
    └── README.md

````

### Step 3
###### Configuring knife

1. Go to [Organizations](https://manage.opscode.com/organizations) area and **select** the organization to be active.
2. Click to Download ***Generate knife config*** 
3. Click to Download ***  Regenerate validation key ***
4. Go to your [Profile](https://www.opscode.com/account/profile)
5. Go to [Change Password](https://www.opscode.com/account/password) and click to Download your private key (**Get a new key** Button)

Copy all 3 files to the chef-repo/.chef directory

````
~/chef/chef-repo $ cp ~/Downloads/yourorganization-validator.pem .chef
~/chef/chef-repo $ cp ~/Downloads/tdantas.pem .chef
~/chef/chef-repo $ cp ~/Downloads/knife.rb .chef

````  

### Step 4
###### Connecting with the chef-server

Now, we are able to connect with the Chef-Server.

Let´s do it.

Knife will lookup for the ***knife.rb*** in 3 different locations.

1. .chef inside your current directory
2. In the $HOME/.chef directory
3. In the /etc/chef directory  

````
Inside the current directory, we have the .chef with all configuration

~/chef/chef-repo $ knife client list
  #=> yourorganization-validator

````
 


   