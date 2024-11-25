# 2420 Assignment 3 part 1

Hey new user, this tutorial will help you set up an HTML generator that runs everyday at 5:00 am. All the necessary files are found in this repo, all you need to do is follow this tutorial to configure your Arch Linux to run the files for success!

## 1. Creating a new System User (Webgen)

For this setup, you will need to create a new user named "webgen" for which the files have been geared to execute towards. They have been written this way to ensure security (limiting access in case of security breach) and efficiency (blank slate solely intended for these setup files) are met for the execution of this tutorial.

This user will have a home directory set to /var/lib/webgen and will not have a login shell (since it will not be used for interactive logins). 

To execute, run this command: 

sudo useradd --system -d /var/lib/webgen -s /usr/sbin/nologin webgen

- --system: Creates a system user
- -d /var/lib/webgen: Sets home directory for the user
- -s /usr/sbin/nologin: Prevents user from logging in through command line

Next we will need to create the necessary subdirectories for files we will be integrating later. 
We will need to make subdirectories for Bin and HTML, we can do this with the following commands: 

sudo mkdir /var/lib/webgen/HTML
sudo mkdir /var/lib/webgen/bin

Additionally, we will need to make this new user the owner of this directory. 

To execute, run this command:

sudo chown -R webgen:webgen /var/lib/webgen

- -R: Allows Ownership for all the directories under webgen

## 2. Setting up Necessary Files

The current repository you are in includes all the necessary files. To access these files onto your local machine, execute this command:

git clone https://github.com/philiflo/2420-as3.git

### generate_index

The generate_index script is responsible for generating the html template that will be injected into the index.html file, which we will be calling to create our website. 

To move the file to its proper location, execute the following command inside the 2420-as3 directory:

sudo mv generate_index /var/lib/webgen/bin/

Once executed, make sure the script is executable by running:

sudo chmod +x /var/lib/webgen/bin/generate_index

### generate-index.service and generate-index.timer

The generate-index.service and generate-index.timer file are responsible for the execution of this process daily at 5am. Generate-index.service defines what action must be executed (running the script inside generate_index), while generate-index.timer defines the time in which the file must be executed. 

To move the file to its proper location, execute the following command inside the 2420-as3 directory:

sudo cp generate-index.service /etc/systemd/system/

Once executed, make sure the script is executable by running:

sudo chmod +x /var/lib/webgen/bin/generate_index

Once done, reload systemd through: 

sudo systemctl daemon-reload

Then enable the timer through:

sudo systemctl enable --now generate-index.timer

### nginx.conf and service-block.conf



## 3. Setting up Personal Firewall (UFW)


## Troubleshooting


