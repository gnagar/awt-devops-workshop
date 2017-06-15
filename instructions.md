## Instructions for the refresher workshop

We will use the same Lubuntu VM we had used earlier in the session - the following instructions assume that you have that setup on your individual machines.

### Boot up the VM

- Open VirtualBox (do not upgrade when and if prompted)
- Double click on the workshop VM listed on the left panel
- Follow the below instructions

### Install jre 8 on the VM

Download the jre from here: 
http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jre-8u131-linux-x64.tar.gz

Once downloaded, unzip it to a location (e.g. /home/appworks/Downloads/)

```shell
export PATH=/home/appworks/Downloads/jre1.8.0_131/bin:$PATH
```

Set PATH variable in `.profile` to include Java binary in the terminal

```shell
vi ~/.profile

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin directories
PATH="$HOME/Downloads/jre1.8.0_131/bin:$HOME/bin:$HOME/.local/bin:$PATH"
```

### Install Jenkins on the VM

- Download Jenkins war file in the VM and save it to `/home/appworks/Downloads/`. The LTS version can be found here: http://mirrors.jenkins.io/war-stable/latest/jenkins.war
- On the same terminal whereStart Jenkins from the terminal by issuing the following command `/home/appworks/Downloads/`

### Run the following command on terminal - this is required for ELK stack to run properly

```shell
sudo sysctl -w vm.max_map_count=262144
```
