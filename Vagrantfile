# -*- mode: ruby -*-

# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.require_version ">= 1.5.0"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box     = "ubuntu/xenial64"

  # Turn off shared folders
  config.vm.synced_folder ".", "/vagrant", disabled: true

  config.vm.provision "shell" do |s|
    ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
    s.inline = <<-SHELL
      echo #{ssh_pub_key} >> /home/ubuntu/.ssh/authorized_keys
    SHELL
  end

  # Begin node-1.vagrant
  config.vm.define "node-1.vagrant" do |node1_config|
    node1_config.vm.hostname = "node-1.vagrant"
    node1_config.vm.network :private_network, ip: "192.168.50.10"
  end
  # End node-1.vagrant

  # Begin node-2.vagrant
  config.vm.define "node-2.vagrant" do |node2_config|
    node2_config.vm.hostname = "node-2.vagrant"
    node2_config.vm.network :private_network, ip: "192.168.50.11"
  end
  # End node-2.vagrant

  # Begin node-3.vagrant
  config.vm.define "node-3.vagrant" do |node3_config|
    node3_config.vm.hostname = "node-3.vagrant"
    node3_config.vm.network :private_network, ip: "192.168.50.12"
  end
  # End node-3.vagrant
end
