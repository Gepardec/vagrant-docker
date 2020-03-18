# -*- mode: ruby -*-
# vi: set ft=ruby :

#########################
$CPU = 2
$MEMORY = 2048
$CPUEXECUTIONCAP = 50 # does not work with hyper-v
$IP = "192.168.0.4"   # does not work with hyper-v # https://www.vagrantup.com/docs/hyperv/limitations.html
$BASEOS = "centos/7"
$SSH=2224
#########################

Vagrant.configure("2") do |config|
  config.vm.box = $BASEOS

  config.vm.provider "virtualbox" do |v|
    v.memory = $MEMORY
    v.cpus = $CPU
    v.customize ["modifyvm", :id, "--cpuexecutioncap", $CPUEXECUTIONCAP]
  end

  config.vm.provider "hyperv" do |v|
    v.memory = $MEMORY
    v.cpus = $CPU
  end
  
  config.vm.provider "libvirt" do |v|
    v.memory = $MEMORY
    v.cpus = $CPU
  end
  
  config.vm.network "private_network", ip: $IP
  config.vm.network "forwarded_port", guest: 22, host: $SSH, id: 'ssh'

  config.vm.synced_folder ".", "/vagrant"

  config.vm.provision "ansible_local" do |ansible|
    ansible.galaxy_role_file = "/vagrant/requirements.yml"
    ansible.playbook = "/vagrant/playbook.yml"
  end
  
end
