# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_API = 2

Vagrant.configure(VAGRANT_API) do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.box_check_update = false
  config.vm.network "forwarded_port", guest: 6443, host: 6443, host_ip: "0.0.0.0"
  config.vm.network "public_network"

  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.gui = true
    vb.memory = "2048"
    vb.name = "k3s-master"
  end

  config.vm.provision :docker

  config.vm.provision "shell", inline: <<-SHELL
    sudo modprobe vxlan
    # curl -sfL https://get.k3s.io | sh -
    # hostnamectl set-hostname k3s-master
  SHELL
end
