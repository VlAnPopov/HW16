# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  { :name => "web", :ip => "192.168.56.110", :box => "ubuntu/jammy64", :memory => 2048, :cpus => 2, :ansible => 'web.yml'},
  { :name => "log", :ip => "192.168.56.111", :box => "ubuntu/jammy64", :memory => 2048, :cpus => 2, :ansible => 'log.yml'},
  { :name => "aux", :ip => "192.168.56.112", :box => "ubuntu/jammy64", :memory => 2048, :cpus => 2, :ansible => 'aux.yml'},
 ]

Vagrant.configure("2") do |config|
  boxes.each do |box|
    config.vm.define box[:name] do |target|
      target.vm.provider "virtualbox" do |v|
        v.name = box[:name]
        v.memory = box[:memory]
        v.cpus = box[:cpus]
      end
      target.vm.box = box[:box]
      target.vm.network "private_network", ip: box[:ip]
      target.vm.hostname = box[:name]
      target.vm.synced_folder ".", "/vagrant"
#      target.vm.provision "shell", path: box[:script]
      if box.key?(:ansible) 
        target.vm.provision "ansible" do |ansible|
          ansible.playbook = box[:ansible]
        end
      end
    end
  end
end