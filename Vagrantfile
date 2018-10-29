# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/xenial64"

  config.vm.provider "virtualbox" do |vb|
     vb.memory = "2048"
  end

  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
  end

  config.vm.define "node01" do |node|
    node.vm.hostname = "node01"
    node.vm.network :private_network, ip: "192.168.100.11"
  end

  config.vm.define "node02" do |node|
    node.vm.hostname = "node02"
    node.vm.network :private_network, ip: "192.168.100.12"
  end

  config.vm.define "node03" do |node|
    node.vm.hostname = "node03"
    node.vm.network :private_network, ip: "192.168.100.13"
  end
  
end
