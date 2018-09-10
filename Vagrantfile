# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # DEV DESKTOP BOX
  config.vm.define "dev" do |dev|
    dev.vm.box = "debian/stretch64"
    dev.vm.network "private_network", ip: "192.168.143.10"
    dev.vm.synced_folder "shared/sql", "/home/vagrant/sql"
    # dev.vm.synced_folder "shared/src", "/home/vagrant/src"
    dev.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    dev.vm.provision "shell" do |root|
      root.path = "provision/dev_root.sh"
      root.privileged = true
    end
    dev.vm.provision "shell" do |user|
      user.path = "provision/dev_user.sh"
      user.privileged = false
    end
  end

  # DATABASE BOXES
  config.vm.define "db1" do |db1|
    db1.vm.box = "centos/7"
    db1.vm.network "private_network", ip: "192.168.143.200"
    db1.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
    end
    db1.vm.provision "shell" do |root|
      root.path = "provision/db_root.sh"
    end
  end

  # APP BOXES
  config.vm.define "app1" do |app1|
    app1.vm.box = "centos/7"
    app1.vm.network "private_network", ip: "192.168.143.100"
    app1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
    end
    app1.vm.provision "shell" do |s|
      s.path = "provision/app_root.sh"
    end
  end

  # APPLY TO ALL BOXES
  config.vm.synced_folder "shared/xfer", "/home/vagrant/xfer"
end
