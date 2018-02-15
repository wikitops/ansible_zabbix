# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "ubuntu/xenial64"

  # Zabbix Server
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "zabbix0#{i}" do |server|
      server.vm.hostname = "zabbix0#{i}"
      server.vm.network "private_network", ip: "10.0.0.17#{i}"
    end
  end

  # Postgresql
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 2048
      vb.cpus = 2
    end

    config.vm.define "postgresql0#{i}" do |server|
      server.vm.hostname = "postgresql0#{i}"
      server.vm.network "private_network", ip: "10.0.0.18#{i}"
    end
  end

  # Node
  (1..1).each do |i|
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end

    config.vm.define "node0#{i}" do |server|
      server.vm.hostname = "node0#{i}"
      server.vm.network "private_network", ip: "10.0.0.19#{i}"
    end
  end

  # Provision
  config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "/home/vagrant/.ssh/authorized_keys"

end
