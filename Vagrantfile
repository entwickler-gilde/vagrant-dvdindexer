# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.hostname = "dvdindex"
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "dvdindex"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/precise/current/precise-server-cloudimg-amd64-vagrant-disk1.box"
  config.vm.provider "virtualbox" do |vb|
    vb.name = "dvdindex"
    vb.memory = 1024
    vb.cpus = 1
    vb.customize ["storagectl", :id, "--name", "IDE Controller", "--add", "ide"]
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "0", "--device", "0", "--type", "dvddrive", "--medium", "emptydrive"]
# optional for HW DVD - comment above line then.
#    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "0", "--device", "0", "--type", "dvddrive", "--medium"]
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "0", "--device", "1", "--type", "dvddrive", "--medium", "emptydrive"]
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "1", "--device", "0", "--type", "dvddrive", "--medium", "emptydrive"]
    vb.customize ["storageattach", :id, "--storagectl", "IDE Controller", "--port", "1", "--device", "1", "--type", "dvddrive", "--medium", "emptydrive"]
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.become = true
    ansible.limit = 'all'    
  end  
end