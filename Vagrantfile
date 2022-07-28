# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = true

  # APACHE SERVICE
  config.vm.define "webapp" do |webapp|
      webapp.vm.hostname = "webapp"
      webapp.vm.network "private_network", ip: "192.168.56.10"
      webapp.vm.provider "virtualbox" do |v|
          v.name = "webapp"
          v.memory = 2048
          v.cpus = 2
          v.linked_clone = true
          v.gui = false
      end

      webapp.vm.provision "shell", inline: <<-SHELL 
        sudo apt update
        sudo apt upgrade -y

        sudo apt install apache2 -y
      SHELL
  end

  # MARIADB 
  config.vm.define "mariadb" do |mariadb|
    mariadb.vm.hostname = "zk1"
    mariadb.vm.network "private_network", ip: "192.168.56.11"
    mariadb.vm.provider "virtualbox" do |v|
          v.name = "mariadb"
          v.memory = 2048
          v.cpus = 1
          v.linked_clone = true
          v.gui = false
      end
      mariadb.vm.provision "shell", inline: <<-SHELL 
        sudo apt update
        sudo apt upgrade -y

        sudo apt install -y mariadb-server
      SHELL
  end
end