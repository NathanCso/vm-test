# Vagrantfile
Vagrant.configure("2") do |config|
  
  config.vm.define "vm1" do |vm1|
    vm1.vm.box = "ubuntu/focal64"         
    vm1.vm.hostname = "vm1"               
    vm1.vm.network "private_network", ip: "192.168.56.11"  

   
    vm1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  end

  
  config.vm.define "vm2" do |vm2|
    vm2.vm.box = "ubuntu/focal64"         
    vm2.vm.hostname = "vm2"
    vm2.vm.network "private_network", ip: "192.168.56.12"  

   
    vm2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  end
end
