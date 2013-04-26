# Chef Menu

![Chef icon](http://docs.opscode.com/_static/opscode_chef_html_logo.png)

## Overview

Every project needs, at least, one person that knows how to configure and install all components that make your infrastructure.

In the IT's vocabulary we call this person as **System Administrators** (SysAdmin). SysAdmins are the hardware's gods in your company, they work in the Operational Department and know how to configure and control your enviroment. Some developers, without hardware's afinity, love this separation of concerns in the organization. In the OOP world is the same as Single Responsability principle. 

Now startups from every corner in the world is fighting for not only developments capabilities. Developer that knows how to configure and tunning the enviroment will shine. This new kid on the block are called **devops**

DevOps is a developer with System Administration's competencies. They will setup your enviroment and you are ready to get traction and make money.

With the DRY ( *Don't Reapeat Yourself* ) principle in mind, Chef was built. Chef is an automation framework that makes it easy to provisioning servers.

Using Chef, we create one **Cookbook** that will contains instructions ( **Recipes** ) to configure your machine ( **Node** ).

**Disclaimer**: IMHO, system administrators are really necessary to Tuning your enviroment/ perform audits routine/OS updates, patchs/ Networking infrastructure/ Security Holes and may others duties that is not the main skill for one developer.


## Chef components

##### Chef Server

Is the main repository for your **cookbooks**. Is the central piece that aggregate informations about all nodes in your network.

There are 3 flavors that you could use:

* Hosted Chef ( Chef as SaaS provided by Opscode)
* Private Chef ( Chef on the premises of the person. Inside your organization.)
* Open Source Chef Server ( Open Source Version that contains much of the same funcionality as Hosted Chef. All fixes, updates you must apply by yourself).


##### Node

A node is whatever host that have one **chef-client** installed. Think as the Target

The node will be provisioned with *recipes* that was configured in the **Chef-Server**.

When you command the provisioning, the **Node** will communicate with the **Chef-Server** using the configured **chef-client**. The chef-client contains the recipe execution environment that will run recipes that you configured in the chef-server for the specific node.

##### Workstation

The workstation is your playground ( Your development machine ). In the workstation you create the cookbooks and upload to the chef-server. 

The workstation talks with the chef-server using the *Knife* command line tool.

Knife is a command-line tool that provides an interface between a local Chef repository ( your workstation directory structure files ) and the Chef-Server. 


![chef Overview](http://docs.opscode.com/_images/overview_chef_draft.png) 











This menu will be composed of 4 parts. Each part will be placed inside your own branch.


### [Part 1.](https://github.com/tdantas/about-chef/tree/part-1)

 **Configuring your Workstation to talk with the Chef-Server**

### Part 2.

  **Configuring Vagrant with the Chef-Client**
  
### Part 3.
  
   **Provisioning Vagrant with nginx / Unicorn**
   
### Part 4.
   
   **Provisioning EC2 instances with Vagrant and Hosted-Chef**
   
   
 
   
