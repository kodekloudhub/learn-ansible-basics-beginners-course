# Install Ansible

## Install

1. Log into the controller machine

    ```
    vagrant ssh ansiblecontroller
    ```

1. Install

    ```bash
    sudo yum install -y ansible
    ```

1. Verify

    ```bash
    ansible --version
    ```

    You should see something similar to this

    ```
    ansible [core 2.14.17]
      config file = /etc/ansible/ansible.cfg
      configured module search path = ['/home/vagrant/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
      ansible python module location = /usr/lib/python3.9/site-packages/ansible
      ansible collection location = /home/vagrant/.ansible/collections:/usr/share/ansible/collections
      executable location = /usr/bin/ansible
      python version = 3.9.18 (main, Jan 24 2024, 00:00:00) [GCC 11.4.1 20231218 (Red Hat 11.4.1-3)] (/usr/bin/python3)
      jinja version = 3.1.2
      libyaml = True
    ```

## Test

Now we will make a small test project

1. Create folder for the project

    ```bash
    mkdir test-project
    cd test-project
    ```

1. Create an inventory file for the target machine `target1`, providing the password to log into it

    ```bash
    echo "target1 ansible_ssh_pass=vagrant" > inventory.txt
    ```

1. Test connectivity

    We can now run a connectivity test by using a module called `ping`. Run the ansbile command specifying the target machine, the ping module and the inventory file

    ```bash
    ansible target1 -m ping -i inventory.txt
    ```

    You should see an ouput like this

    ```
    target1 | SUCCESS => {
        "ansible_facts": {
            "discovered_interpreter_python": "/usr/bin/python3"
        },
        "changed": false,
        "ping": "pong"
    ```

    If you get an error like the following, it means that you did not test the login from `ansiblecontroller` to `target1` and Ansible is not able to do the key validation.

    > Using a SSH password instead of a key is not possible because Host Key checking is enabled and sshpass does not support this.

    If you see this, then first log into the target machine and answer `yes` to the question, then enter the password...

    ```
    [vagrant@ansiblecontroller test-project]$ ssh target1
    The authenticity of host 'target1 (192.168.56.12)' can't be established.
    ED25519 key fingerprint is SHA256:1s1Ud+oggJCN32n1bdoJjgqeov0cSN4H44uQv+o5lJQ.
    This key is not known by any other names
    Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
    Warning: Permanently added 'target1' (ED25519) to the list of known hosts.
    vagrant@target1's password:
    Last login: Wed Jul 31 06:26:54 2024 from 10.0.2.2
    [vagrant@target1 ~]$ exit
    logout
    Connection to target1 closed.
    ```

    Retry the ansible command. It should now work.