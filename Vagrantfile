# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise32"
  # config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Port forwarding for rails server
  config.vm.network :forwarded_port, host: 3000, guest: 3000

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # use host user's global git config files
  config.vm.provision "file", source: "~/.gitconfig", destination: "~/.gitconfig"
  config.vm.provision "file", source: "~/.gitignore_global", destination: "~/.gitignore_global"

  # provisioning with ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "./roles/site.yml"
    ansible.verbose = "vvv"
  end
end
