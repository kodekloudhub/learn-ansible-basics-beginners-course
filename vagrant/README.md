# Build your own Ansible lab

These instructions supersede those found in the appendix of this course so *ignore* those videos as you won't get far. Besides, they tell you to install CentOS 7 which no longer works. The original instructions were created before Apple Silicon Macs (M1, M2, M3) came on the scene and before CentOS 7 was withdrawn by Red Hat.

What is presented here will work for Windows, Intel Mac and Apple Silicon Mac.

Rather than going through the individual steps of manually creating the virtual machines in VirtualBox (which is what does not work on newer Macs), we instead automate the creation of the VMs using Vagrant which can drive both VirtualBox (Windows/Intel Mac) and VMware Fusion (Apple Silicon) from the same inputs.

## Prerequisites

Set up the required software. This instruction *replaces* the video [Demo: Setup Ansible Local Environment - Using VirtualBox](https://learn.kodekloud.com/user/courses/learn-ansible-basics-beginners-course/module/a1ba12c0-66c7-4d81-bede-62917ee0b1cf/lesson/371a5d25-c693-4aaf-a340-050ad961af0d)

### All systems

**Install Vagrant**

1. Go to the [download page](https://developer.hashicorp.com/vagrant/downloads)
1. For Macs:
    * If you have [homebrew](https://brew.sh/) installed (you really should :smile:), follow the **Package manager** instructions, *else*
        * For Intel Mac, download the AMD64 version
        * For Apple Silicon Mac, download the ARM64 version.
        * Both the above will download a DMG package which Finder should offer to install for you
1. For Windows
    * Download the AMD64 version which is a Windows Installer package. Open this file when it's downloaded and Windows Installer will install it.

### Windows/Intel Mac

**Install VirtualBox**

1. Go to the [download page](https://www.virtualbox.org/wiki/Downloads)
1. Click on the platform packages link for your system
    * For Macs, Finder should offer to install the downloaded DMG package for you
    * For Windows, open on the downloaded file to launch the installer.

### Apple Silicon Mac

**Install VMware Fusion**

This is quite fiddly due to the fact that the Broadcom (the owners of VMware) site is like a maze. They keep moving it around therefore it is not practical to have specific instructions here, however the general gist is -

1. Start at https://www.vmware.com/products/desktop-hypervisor/workstation-and-fusion
1. Select Download Fusion or Workstation - you will be redirected to a login page.
1. Register for a new account.
1. Once your account is activated, then find your way to the Fusion Pro download page.
1. Download it and Finder will install it for you

**Install the Vagrant provider for VMware**

* Follow the instructions [here](https://developer.hashicorp.com/vagrant/docs/providers/vmware/installation).

## Start the Virtual Machines

Do all the following from your favourite terminal application

1. Clone this repository

    ```bash
    



