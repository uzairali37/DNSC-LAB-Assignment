# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  #config.vm.box_check_update = true
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--usb", "on"]
    vb.customize ["modifyvm", :id, "--usbehci", "off"]
    vb.customize ["modifyvm", :id, "--nicpromisc2", "allow-all"]
    vb.customize ["modifyvm", :id, "--nicpromisc3", "allow-all"]
    vb.customize ["modifyvm", :id, "--nicpromisc4", "allow-all"]
    vb.customize ["modifyvm", :id, "--nicpromisc5", "allow-all"]
    vb.cpus = 1
  end
  config.vm.define "router-1" do |router1|
    router1.vm.box = "bento/ubuntu-16.04"
    router1.vm.hostname = "router-1"
    router1.vm.network "private_network",ip: "192.168.0.2", netmask: "255.255.252.0",virtualbox__intnet: "broadcast_router-south-1", auto_config: true
    router1.vm.network "private_network",ip: "192.168.0.6", netmask: "255.255.252.0",virtualbox__intnet: "broadcast_router-inter", auto_config: true
    router1.vm.provision "shell", path: "common.sh"
    router1.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
  config.vm.define "router-2" do |router2|
    router2.vm.box = "bento/ubuntu-16.04"
    router2.vm.hostname = "router-2"
    router2.vm.network "private_network",ip: "192.168.0.4", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_router-south-2", auto_config: true
    router2.vm.network "private_network",ip: "192.168.0.3", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_router-inter", auto_config: true
    router2.vm.provision "shell", path: "common.sh"
    router2.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
  config.vm.define "switch" do |switch|
    switch.vm.box = "bento/ubuntu-16.04"
    switch.vm.hostname = "switch"
    switch.vm.network "private_network",ip: "192.168.0.7", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_router-south-1", auto_config: true
    switch.vm.network "private_network",ip: "192.168.8.10", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_host_a", auto_config: true
    switch.vm.network "private_network",ip: "192.168.4.10", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_host_b", auto_config: true
    switch.vm.provision "shell", path: "switch.sh"
    switch.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
  config.vm.define "host-a" do |hosta|
    hosta.vm.box = "bento/ubuntu-16.04"
    hosta.vm.hostname = "host-a"
    hosta.vm.network "private_network",ip: "192.168.8.11", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_host_a", auto_config: true
    hosta.vm.provision "shell", path: "common.sh"
    hosta.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
  config.vm.define "host-b" do |hostb|
    hostb.vm.box = "bento/ubuntu-16.04"
    hostb.vm.hostname = "host-b"
    hostb.vm.network "private_network",ip: "192.168.4.11", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_host_b", auto_config: true
    hostb.vm.provision "shell", path: "common.sh"
    hostb.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
  config.vm.define "host-c" do |hostc|
    hostc.vm.box = "bento/ubuntu-16.04"
    hostc.vm.hostname = "host-c"
    hostc.vm.network "private_network",ip: "192.168.0.12", netmask: "255.255.252.0", virtualbox__intnet: "broadcast_router-south-2", auto_config: true
    hostc.vm.provision "shell", path: "common.sh"
    hostc.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
    end
  end
end
