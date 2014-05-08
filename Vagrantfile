# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "hashicorp/precise32"

  # Port forwarding for rails server
  config.vm.network :forwarded_port, host: 3000, guest: 3000
  
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end

  # use host user's gitconfig file
  config.vm.provision "file", source: "~/.gitconfig", destination: "~/.gitconfig"
  # provisioning with ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "./ansible/playbook.yml"
    #ansible.verbose = "vvvv"
  end
end
