This repository holds different vagrantfiles and associated provisioning for various setups I've needed.

### Get Up and Running

1. Install [Virtual Box][1]
1. Install [Vagrant][2] or the gem:

    gem install vagrant
1. Install [Ansible][3]

    brew install ansible
1. Drop the Vagrantfile, the ansible directory, and ansible.cfg file into your project directory.
1. Update the project-specific variables in roles/common/vars/main.yml.
1. Spin up the box

    vagrant up
1. SSH to the new vagrant box

    vagrant ssh

You will be logged in as the vagrant user. Your project directory will be shared to /vagrant.    

[1]: https://www.virtualbox.org/wiki/Downloads
[2]: http://www.vagrantup.com/
[3]: http://www.ansible.com/
