# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  config.vm.host_name = "djangobox"
  config.ssh.forward_agent = true

  # Shared folders
  hosthome = "#{ENV['HOME']}/"
  config.vm.synced_folder "../django", "/django", type: "nfs"
  config.vm.synced_folder hosthome, "/home/vagrant/.hosthome"

  # Host-only network required to use NFS shared folders
  config.vm.network "private_network", ip: "1.2.3.4"

  config.vm.provider "virtualbox" do |vb|
    vb.name = "djangobox"
    vb.gui = false
    vb.memory = 2048
    vb.cpus = 2
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
