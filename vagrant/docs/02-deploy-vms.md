# Deploying the Virtual Machines

Do all the following from your favourite terminal application

1. Clone this repository

    ```bash
    git clone https://github.com/kodekloudhub/learn-ansible-basics-beginners-course.git
    ```

1. Change to `vagrant` directory

    ```bash
    cd vagrant
    ```

1. Start the virtual machines.

    ```bash
    vagrant up
    ```

    Soon after the process starts, it will display a box like this. If you need to raise questions on our forums about the VM installation, you *must* copy this output from your system and include it with your message so we can help you better.

    ```text
    ┌─────────────────────────── EXAMPLE ─────────────────────────────────┐
    │ If raising a question on our forums, please include the contents    │
    │ of this box with your question. It will help us to identify issues  │
    │ with your system.                                                   │
    │                                                                     │
    │ Detecting your hardware...                                          │
    │ - System: Microsoft Windows 10 Enterprise                           │
    │ - CPU:    Intel(R) Core(TM) i7-7800X CPU @ 3.50GHz (12 cores)       │
    │ - RAM:    32 GB                                                     │
    └─────────────────────────────────────────────────────────────────────┘
    ```

    When the process completes successfully, it will display the names of the VMs and their IP addresses on the virtual network

    ```text
    192.168.56.11 ansiblecontroller
    192.168.56.12 target1
    ```

    Note that the login credentials for all these machines is

    ```
    Username: vagrant
    Password: vagrant
    ```

4. Test logging in.

    1. Log into the controller VM

        ```
        vagrant ssh ansiblecontroller
        ```

        This login is password-less so you should get directly to the CentOS prompt.

    1. Test the controller can connect to the target machine

        ```
        ssh target1
        ```

        You will be asked for the password this time, which is the password above.

    1. Enter `exit` command twice to retun to laptop command prompt.

## Deleting the VMs

To erase all VMs, do

```
vagrant destroy -f
```

Next: [Install Ansible](./03-install-ansible.md)<br/>
Prev: [Prerequisites](./01-prerequisites.md)

