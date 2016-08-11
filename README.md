Description
=========

This is a ansible tutorial.

### TAG: ADHOC
At this point there is a simple Vagrant file and a hosts file.  The Vagrant box is Centos 7.2.

Note:  You probabaly want to disable host key checking with ssh.
See http://docs.ansible.com/ansible/intro_getting_started.html

### TAG: PLAYBOOK-EXAMPLE

We add a group to the inventory file (hosts) and write a simple playbook.
We also add a template file and an ansible.cfg.

Try running
```bash
vagrant up
ssh-agent bash
ssh-add .vagrant/machines/default/virtualbox/private_key
ansible all -i hosts -u vagrant -m ping
ansible all -i hosts -u vagrant -m yum -a "name=vim-enhanced state=present" --sudo
ansible all -i hosts -u vagrant -a "yum info vim-enhanced" --sudo
```

### TAG: ROLES-EXAMPLE

Here we show some best practices and move tasks to a role.

- We added the ansible provisioner to the Vagrantfile and removed the original inventory file (hosts)
  - Vagrant will now create a inventory file and call ansible-playbook automatically
  - `vagrant up` will bring the machine up and run the provisioner once
  - `vagrant provision` will run ansible if the vm is already loaded
- We added roles and moved the ntp tasks and variables in to the appropriate files
- We added tags to the ntp role tasks
- We added an include statement in site.yml

Try running
```bash
vagrant up
# After the provisioner runs, you can run it again
vagrant provision
```

### TAG: GALAXY-EXAMPLE

We removed the ntp role and put it in a public repo to share!

Try running:
```bash
mkdir galaxy-roles
ansible-galaxy install -r install_roles.yml
vagrant up
# or vagrant provision if the vm is still up
```

Requirements
------------
This tutorial was written using:
* ansible 2.0.1.0
* vagrant 1.8.1
* VirtualBox 5.0.16

