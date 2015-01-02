# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  config.vm.box = "oraclelinux-6-x86_64"
  config.vm.box_url = "http://cloud.terry.im/vagrant/oraclelinux-6-x86_64.box"
  config.vm.hostname = "oracle"

  config.ssh.forward_x11=true

  # Forward Oracle ports
  config.vm.network :forwarded_port, guest: 1521, host: 1521
  config.vm.network :forwarded_port, guest: 1522, host: 1522
  config.vm.network :forwarded_port, guest: 1158, host: 1158
  config.vm.network :forwarded_port, guest: 2484, host: 2484
  config.vm.network :forwarded_port, guest: 22, host: 2222, host_ip: "0.0.0.0", id: "ssh", auto_correct: true 
  #config.vm.network "public_network"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id,
                  "--memory", "2048",
                  "--natdnshostresolver1", "on"]
  end

  config.vm.provision :shell, :inline => "sudo rm /etc/localtime && sudo ln -s /usr/share/zoneinfo/US/Eastern /etc/localtime"

  config.vm.provision :shell, :inline => "sudo yum install puppet -y"

  #config.vbguest.auto_update = false

  config.vm.provision :puppet do |puppet|
    puppet.manifests_path = "manifests"
    puppet.module_path = "modules"
    puppet.manifest_file = "base.pp"
    puppet.options = "--verbose --trace"
  end
end
