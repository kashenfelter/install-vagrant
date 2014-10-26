
# Tessera with Vagrant #

Vagrant provides a lightweight mechanism to provision a reproducible portable Tessera environment for testing and development.  This is the easiest way to get a local platform-independent single-node VM with the Hadoop-backed Tessera environment installed.

The subdirectories in this repository provide scripts to provision a Tessera Vagrant VM with various versions of Tessera components.  The current recommended environment is `cdh4mr1-rhipe0.74`.

## Provisioning a VM ##
*****

Download and install Vagrant: http://www.vagrantup.com/downloads.html

On a command line, clone this repository:

````
git clone https://github.com/tesseradata/install-vagrant
````

Choose the directory in this repository with the environment you would like, for example

````
cd install-vagrant/cdh4mr1-rhipe0.74
````

This will put you in an environment with CDH4 running MapReduce version 1 and with RHIPE 0.74.

To provision the environment, simply type the following:

````
vagrant up
````

If you are testing cdh5mr2-Rhipe0.75 please use the following instead of just vagrant up,
````
vagrant up --provider=aws
````
for aws as the provider, or for local virtualbox use,

````
vagrant up --provider=virtualbox
````

Once the provisioning has completed

* To work from command line: SSH into the machine with `vagrant ssh`
* To work from RStudio IDE: navigate to `localhost:9787` in your web browser with credentials vagrant:vagrant
* To work with cdh5mr2-Rhipe0.75 or AWS use `ssh -i key ubuntu@hostname` or (if username is different than ubuntu) `ssh -i key user@hostname`.
* While using cdh5-mr2-Rhipe0.75, to access all HTTP pages on your AWS machine tunnel your traffic the following way `ssh -D 10009 -i key ubuntu@hostname` or `ssh -D 10009 -i key username@hostname`
* To work with cdh5mr2-Rhipe.075 on a local machine use `ssh -p 2202 ubuntu@localhost` or `ssh -p 2202 username@localhost`


Unless otherwise noted in the README file for a specific installation, the following Hadoop services are available at the following locations:

* NameNode: `http://localhost:60070`
* JobTracker: `http://localhost:60030`
* TaskTracker: `http://localhost:60060`

## Bugs
* `vagrant ssh` does not work with cdh5mr2-Rhipe0.75. Please do not use it. See how to use SSH for cdh5mr2-Rhipe0.75 above.  
