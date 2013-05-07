# Chef Menu

![Chef icon](http://docs.opscode.com/_static/opscode_chef_html_logo.png)

## Overview

Every project needs at least one person that knows how to configure and install all components that make your infrastructure.

Using IT vocabulary, this person is called a **System Administrator** (SysAdmin). SysAdmins are the hardware gods in your company. They work in the Operational Department and know how to configure and control your environment. Some developers, without hardware afinity, love this separation of concerns in the organization. In the OOP world it is the same as the Single Responsability principle. 

Now, startups from every corner of the world aren't fighting only for development capabilities. Developers that know how to configure and tune the environment will shine. This new kid on the block is called **devops**.

DevOps is a developer with System Administration's competencies. They will setup your enviroment and get you ready to get traction and make money.

With the DRY ( *Don't Repeat Yourself* ) principle in mind, Chef was built. Chef is an automation framework that makes it easy to provision servers.

Using Chef, we create one **Cookbook** that will contain instructions ( **Recipes** ) to configure your machine ( **Node** ).

**Disclaimer**: IMHO, system administrators are really necessary to tune your enviroment/ perform audit routines/OS updates, patches/ Networking infrastructure/ Security Holes and many other duties that are not the main skills for a developer.


## Chef components

##### Chef Server

This is the main repository for your **cookbooks**. It's the central piece that aggregates information about all nodes in your network.

There are 3 flavors that you could use:

* Hosted Chef ( Chef as SaaS provided by Opscode)
* Private Chef ( Chef on the premises of the company. Inside your organization.)
* Open Source Chef Server ( Open Source Version that contains much of the same funcionality as Hosted Chef. All fixes and updates must be applied by yourself).


##### Node

A node is any host that has one **chef-client** installed. Think of it as the Target.

The node will be provisioned with *recipes* that are configured in the **Chef-Server**.

When you command the provisioning, the **Node** will communicate with the **Chef-Server** using the configured **chef-client**. The chef-client contains the recipe execution environment that will run recipes that you configured in the chef-server for the specific node.

##### Workstation

The workstation is your playground ( Your development machine ). In the workstation you create the cookbooks and upload them to the chef-server. 

The workstation talks with the chef-server using the *Knife* command-line tool.

*Knife* is a command-line tool that provides an interface between a local Chef repository ( your workstation directory structure files ) and the Chef-Server. 


![chef Overview](http://docs.opscode.com/_images/overview_chef_draft.png) 











This menu will be composed of 4 parts. Each part will be placed inside its own branch.


### [Part 1.](https://github.com/tdantas/about-chef/tree/part-1)

 **Configuring your Workstation to talk with the Chef-Server**

### Part 2.

  **Configuring Vagrant with the Chef-Client**
  
### Part 3.
  
   **Provisioning Vagrant with nginx / Unicorn**
   
### Part 4.
   
   **Provisioning EC2 instances with Vagrant and Hosted-Chef**
   
   
 
   
