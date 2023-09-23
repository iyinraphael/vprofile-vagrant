# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true

 ### DB vm ###
  config.vm.define "db01" do |db01|
    db01.vm.box = "generic/centos9s"
    db01.vm.hostname = "db01"
    db01.vm.network "private_network", ip: "192.168.56.15"
    db01.vm.provider "virtualbox" do |vb|
      vb.memory = "600"
    end
      db01.vm.provision "shell", path: "mysql.sh"
  end

 ### Memcache vm ###
      config.vm.define "mc01" do |mc01|
        mc01.vm.box = "generic/centos9s"
        mc01.vm.hostname = "mc01"
        mc01.vm.network "private_network", ip: "192.168.56.14"
        mc01.vm.provider "virtualbox" do |vb|
          vb.memory = "600"
        end
          mc01.vm.provision "shell", path: "memcache.sh"
      end

   ### RabbitMQ vm ###
    config.vm.define "rm01" do |rm01|
      rm01.vm.box = "generic/centos9s"
      rm01.vm.hostname = "rm01"
      rm01.vm.network "private_network", ip: "192.168.56.13"
      rm01.vm.provider "virtualbox" do |vb|
        vb.memory = "600"
      end
        rm01.vm.provision "shell", path: "rabbitmq.sh"
    end

   ### Tomcat vm ###
    config.vm.define "app01" do |app01|
      app01.vm.box = "generic/centos9s"
      app01.vm.hostname = "app01"
      app01.vm.network "private_network", ip: "192.168.56.12"
      app01.vm.provision "shell", path: "tomcat.sh"
      app01.vm.provider "virtualbox" do |vb|
        vb.memory = "800"
      end
    end

     ### Nginx vm ###
      config.vm.define "web01" do |web01|
        web01.vm.box = "ubuntu/jammy64"
        web01.vm.hostname = "web01"
        web01.vm.network "private_network", ip: "192.168.56.11"
        web01.vm.provider "virtualbox" do |vb|
          vb.memory = "800"
        end
          web01.vm.provision "shell", path: "nginx.sh"
      end
end
