# First Virtual Box, Vagrant Dev Environment

This repo is our first virtual Environment to create a dev environment

#### What is a Dev Environment?
A development environment in software and web development is a workspace for developers to make changes without breaking anything in a live environment.

## Virtual box
What is VirtualBox? 
VirtualBox is a virtualisation tool which allows users to run multiple guest operating systems on a single machine

Why does VirtualBox matter? 
VirtualBox makes it possible for administrators and developers to quickly spin up full-blown operating systems without having to use dedicated hardware, thereby saving precious budget dollars on hardware.
Developers are also affected by VirtualBox, as it enables them to develop on a variety of platforms and create virtual networks to further test their software

## Vagrant
What is it?
Vagrant allows the user to build and manage virtual environments in a single workflow. It has a focus on automation which will lower the dev environment set up time, and allow the developer to test if
something will work on multiple operating systems without changing computer.

Vagrant boxes - pre loaded vagrant files that create virtual machines. Usually just an OS

Ubuntu is an open source OS
Ubuntu with GUI (Graphical User Interface)
Ubuntu headless - is basically a terminal, no GUI
    - Faster
    - Lighter
    - More Secure

### Main Commands
- ```vagrant init```
- ```vagrant init <box>``` search for boxes in http://app.vagrantup.com/
- ```vagrant up```
- ```vagrant destroy```

### Linux ubuntu
- sudo apt-get update
    - updates source list

### Task 1
- Vagrant up with ubuntu/xenial64
- Vagrant destroy
- Delete your vagrant file
- Use vagrant init to create vagrant file with centos 7
- Vagrant up again
- Vagrant destroy

#### Solution
- The first thing you need to do is to create a VagrantFile inside the directory you wish to work from. This is achieved by entering ``` vagrant init ``` into your git bash within the directory that you want to set up your dev environment into.
- Then, enter the following code into your VagrantFile. This will allow you to choose which OS you wish to use for your dev environment.
```
Vagrant.configure("2") do |config|
  config.vm.box = "<chosen OS>"
end
```
- Using gitbash, enter ```vagrant up``` to start vagrant.

- Inside can use bash (ls, ll, cd, mkdir, rm, rm -rf, ls , -a)

- ``` vagrant destroy ``` is used to delete the dev environment and will also delete any files that were created 

### Task 2
- Create a vagrant box with ubuntu version 18.04
- Find the command to SSH into the machine
- Create a README.md file inside machine and write your name and your favourite movie

#### Solution
- to create a vagrant box with ubuntu 18.04, ```config.vm.box = "<chosen OS>``` where chosen os is replaced with  "ubuntu/xenial64"
- ``` vagrant up ``` is used to create the vagrant box.
- the command ``` vagrant ssh ``` is used to SSH into the machine.
- to create a README.md file we use the git command ``` touch README.md ``` whilst an SSH connection is established with our vagrant box


### Set up nginx
- First, we need to modify our Vagrantfile like so
```
Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.network = ("private_network", ip: "192.168.10.2")
  config.vm.hostname = "development.local"
end
```
- The following commands are run inside git before using SSH connection
```
sudo apt-get install nginx

sudo apt-get update 

sudo apt-get install nginx
```

- ``` vagrant reload ``` is used to reload the vagrant box
