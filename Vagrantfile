# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Port forwarding for rails server
  config.vm.network :forwarded_port, host: 3000, guest: 3000

  config.vm.network "private_network", ip: "192.168.50.4"

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id,
                  "--name", 'rails-dev-box',
                  "--memory", "1024",
                  "--nictype1", "Am79C973",
                  "--nictype2", "Am79C973",
                  "--natdnshostresolver1", "on"]
  end

  # Set up SSH agent forwarding.
  config.ssh.forward_agent = true

  config.vm.synced_folder ".", "/vagrant", :nfs => true
  config.nfs.map_uid = Process.uid
  config.nfs.map_gid = Process.gid

  # use host user's global git config files
  config.vm.provision "file", source: "~/.gitconfig", destination: "~/.gitconfig"
  config.vm.provision "file", source: "~/.gitignore_global", destination: "~/.gitignore_global"
  # use host user's ssh config file
  config.vm.provision "file", source: "~/.ssh/config", destination: "~/.ssh/config"

  # provisioning with ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "./roles/site.yml"
    #ansible.verbose = "vvv"
  end
end
