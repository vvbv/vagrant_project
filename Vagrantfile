# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

# Configuracion de boxes
  
  # Box 1: web1
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/trusty64"
    web1.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    web1.vm.synced_folder "www_1/", "/var/www/html/www_1"
    web1.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--name', 'web1']
      vb.customize ['modifyvm', :id, '--cpus', '1']
      vb.customize ['modifyvm', :id, '--memory', '720']
      vb.customize ['modifyvm', :id, '--cpuexecutioncap', '50']
    end
  end

  # Box 2: web2
  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/trusty64"
    web2.vm.network "forwarded_port", guest: 80, host: 8008, host_ip: "127.0.0.1"
    web2.vm.synced_folder "www_2/", "/var/www/html/www_2"
    web2.vm.provider "virtualbox" do |vb|
      vb.customize ['modifyvm', :id, '--name', 'web2']
      vb.customize ['modifyvm', :id, '--cpus', '1']
      vb.customize ['modifyvm', :id, '--memory', '720']
      vb.customize ['modifyvm', :id, '--cpuexecutioncap', '50']
    end
  end

  # Habilitar aprovisionamiento desde un script propio: se ejecuta sobre los dos boxes
  config.vm.provision "shell", path: "myscript.sh"
end
