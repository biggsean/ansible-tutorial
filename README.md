Description
=========

This is a ansible tutorial.

TAG: ADHOC
At this point there is a simple Vagrant file and a hosts file.  The Vagrant box is Centos 7.2.

Try running
```bash
vagrant up
ssh-agent bash
ssh-add .vagrant/machines/default/virtualbox/private_key
ansible all -i hosts -u vagrant -m ping
ansible all -i hosts -u vagrant -m yum -a "name=vim-enhanced state=present" --sudo
ansible all -i hosts -u vagrant -a "yum info vim-enhanced" --sudo
```
Note:  You probabaly want to disable host key checking with ssh.
See http://docs.ansible.com/ansible/intro_getting_started.html

Requirements
------------
This tutorial was written using:
ansible 2.0.1.0
vagrant 1.8.1
VirtualBox 5.0.16

