# 2420 Assignment 3 part 1

Hey new user, this tutorial will help you set up an HTML generator that runs everyday at 5:00 am. All the necessary files are found in this repo, all you need to do is follow this tutorial to configure your Arch Linux to run the files for success!

## 1. Creating a new System User (Webgen)

For this setup, you will need to create a new user named "webgen" for which the files have been geared to execute towards. They have been written this way to ensure security (limiting access in case of security breach) and efficiency (blank slate solely intended for these setup files) are met for the execution of this tutorial.

This user will have a home directory set to /var/lib/webgen and will not have a login shell (since it will not be used for interactive logins). 

To execute, run this command: 

sudo useradd --system -d /var/lib/webgen -s /usr/sbin/nologin webgen

- --system: Creates a system user (UID below 1000).
- -d /var/lib/webgen: Sets the home directory for the user.
- -s /usr/sbin/nologin: Prevents the user from logging in interactively.

Next we will need to create the necessary subdirectories for files we will be integrating later. 
We will need to make subdirectories for Bin and HTML, we can do this with the following commands: 

sudo mkdir /var/lib/webgen/HTML
sudo mkdir /var/lib/webgen/bin

Additionally, we will need to make this new user the owner of this directory. 

To execute, run this command:

sudo chown -R webgen:webgen /var/lib/webgen


## 2. Setting up Necessary Files

The current repository you are in includes all the necessary files. To access these files onto your local machine, execute this command:



### generate_index

### generate-index.service and generate-index.timer

### nginx.conf and service-block.conf


## 3. Setting up Personal Firewall (UFW)


