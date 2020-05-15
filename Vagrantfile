# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "./app", "/var/www/html"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "256"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/site.yml"
    ansible.inventory_path = "ansible/hosts"
    ansible.limit = 'all'
  end

  config.vm.provision "shell", run: "always", inline: <<-SHELL
    sudo service httpd restart
  SHELL
end
