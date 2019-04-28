# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "centos/7"

  config.vm.network "private_network", ip: "192.168.56.11"

  # share playbook
  config.vm.synced_folder "./data", "/vagrant"

  # disable to update vagrant-vbguest plugin automatically
  if Vagrant.has_plugin?("vagrant-vbguest") then
    config.vbguest.auto_update = false
  end

  config.vm.provider "virtualbox" do |vb|
     vb.gui = true
     vb.memory = "2048"
  end

  config.vm.provision "ansible_local" do |ansible|
    # playbook.yml is deployed at /vagrant/data/playbook/playbook.yml on guest
    ansible.playbook = "./playbook/playbook.yml"
    ansible.limit = "all"
  end
end
