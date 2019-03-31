# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"
  
  config.vm.provision :shell, path: "scripts/install-postfix.sh"
  config.vm.provision :shell, path: "scripts/install-spamassassin.sh"
  config.vm.define "dev" do |dev|
    dev.vm.network "public_network", type: "dhcp"
    dev.vm.host_name = "simplemail"
    dev.vm.network :forwarded_port, guest: 2333, host: 2333, auto_correct: true
  end
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.cpus = 2
    vb.memory = "2048"
  end
end
