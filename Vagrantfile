# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  
  # DEV DESKTOP BOX
  config.vm.define "dev" do |dev|
    dev.vm.box = "debian/stretch64"
    dev.vm.network "private_network", ip: "192.168.144.10"
    dev.vm.synced_folder "shared/sql", "/home/vagrant/sql"
    dev.vm.synced_folder "shared/src", "/home/vagrant/src"
    dev.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  #   dev.vm.provision "shell", inline: <<-SHELL
  #     apt-get update
  #     apt-get install pyenv
  #     apt-get 
  #   SHELL
  end
  
  # DATABASE BOXES
  config.vm.define "db1" do |db1|
    db1.vm.box = "centos/7"
    db1.vm.network "private_network", ip: "192.168.144.200"
    db1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
  end

  # APP BOXES
  config.vm.define "app1" do |app1|
    app1.vm.box = "centos/7"
    app1.vm.network "private_network", ip: "192.168.144.100"
    app1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
  end

  # APPLY TO ALL BOXES
  config.vm.synced_folder "shared/xfer", "/home/vagrant/xfer"
end
