# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "opensuse/Tumbleweed.x86_64"

  # Forwarded ports
  config.vm.network "forwarded_port", guest: 80, host: 80, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 5000, host: 5000, host_ip: "127.0.0.1"
  
  config.vm.provider "virtualbox" do |vb|
    # the machine name
    vb.name = "flaskapp-POC"
  end

  # install apache and flask
  config.vm.provision "file", source: "localhost.conf", destination: "/home/vagrant/localhost.conf"
  config.vm.provision "file", source: "app.py", destination: "/home/vagrant/app.py"
  config.vm.provision "file", source: "gunicorn.conf", destination: "/home/vagrant/gunicorn.conf"
  config.vm.provision "file", source: "flaskapp.service", destination: "/home/vagrant/flaskapp.service"
  config.vm.provision "shell", path: "install.sh"

end
