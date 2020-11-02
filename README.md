# Spark VM tutorial

This tutorial presents how to create a Linux Ubuntu Virtual Machine (with Ubuntu 20.04) and to install Spark into it.

It assumes that you have Virtual Box or another VM hypervisor installed on your system.

The main steps to obtain a working install of Spark are:
- Installing Ubuntu Server
- Installing required packages in the new install
- Installing Spark

# Installing Ubuntu Server

## Downloading the iso

To download Ubuntu Server, use the following link: https://ubuntu.com/download/server and choose option 3

## Creating the VM

Create a new VM using the downloaded ISO. 
- Most default parameters can be kept
- Don't add any additional package
- The configuration I used for the VM:
  + Memory: 5000MB
  + Disk: 10GB


# Installing required packages in the new install

Install a graphical interface as described here: https://linuxconfig.org/how-to-install-minimal-gnome-on-ubuntu-20-04-focal-fossa-linux

```
sudo apt install gnome-session gnome-terminal 
sudo reboot
```

Installing packages required by Spark
```
sudo apt install openjdk-8-jdk
sudo apt install scala
sudo apt install python-is-python3
```

Install a file manager
```
sudo apt install nautilus
```

If you want to work with Scala, you will further need to install *sbt*. Follow instructions here: https://www.scala-sbt.org/1.x/docs/Installing-sbt-on-Linux.html#Ubuntu+and+other+Debian-based+distributions

```
echo "deb https://dl.bintray.com/sbt/debian /" | sudo tee -a /etc/apt/sources.list.d/sbt.list
curl -sL "https://keyserver.ubuntu.com/pks/lookup?op=get&search=0x2EE0EA64E40A89B84B2DF73499E82A75642AC823" | sudo apt-key add
sudo apt-get update
sudo apt-get install sbt
```

Install any additional packages you would like (text editor, web browser, etc.)
```
sudo apt install emacs
sudo apt install firefox
```

Also install the virtualbox guest additions for a more user friendly experience, as described here: https://linuxhint.com/install_virtualbox_guest_additions_ubuntu/

# Installing Spark

From this point, you can simply follow the tutorial for a native Spark install Linux provided in the DMLSDS course: [https://tropars.github.io/downloads/lectures/LSDM/LSDM-install-spark.pdf](https://tropars.github.io/downloads/lectures/LSDM/LSDM-install-spark.pdf)

Note that by default, scala-11 is installed on your system. In this case, if you want to program in scala, you should install version 2.4.7 of Spark instead of version 3.0.1 as described in the tutorial.
