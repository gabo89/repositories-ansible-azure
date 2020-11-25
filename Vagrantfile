
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
N = 2
(1..N).each do |machine_id|
  config.vm.define "maquina#{machine_id}" do |machine|
    	machine.vm.box = "centos/7"
        machine.vm.hostname = "red-node-#{machine_id}"
    	machine.vm.network "private_network", ip: "192.168.30.#{20+machine_id}"
    	machine.ssh.forward_agent = true
	machine.vm.box_check_update = false
	machine.ssh.username = 'vagrant'
	#machine.ssh.password = 'vagrant'
	machine.ssh.insert_key = 'true'
	machine.vbguest.auto_update = false
	machine.vm.synced_folder ".", "/vagrant", disabled: true
	#puts("enter once")	
    	machine.vm.provider "virtualbox" do |vb|
        #total cpu in my pc = 8 
        vb.cpus = 2
        vb.memory = 8192
        vb.gui = false
        vb.name = "red-node-#{machine_id}"
    	
        #https://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvm
        #vb.customize "pre-boot",["modifyvm", :id, "--nictype1", "Am79C973"]
        #vb.customize "pre-boot",["modifyvm", :id, "--cableconnected1", "on"]
		#puts("enter twice")	

    end
	
		  
    # Only execute once the Ansible provisioner,
    # when all the machines are up and ready.
    #if machine_id == N
    #  machine.vm.provision :ansible do |ansible|
    #    ansible.limit = "all"
    #    ansible.playbook = "playbook.yml"
    #    ansible.verbose = true
    #	ansible.host_key_checking = false
    #  end
    #end 
	
  end
end
end

