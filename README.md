# Provisioning like a Chef - Part 1
### Configuring your workstation to talk with the Chef-Server.

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
 


   