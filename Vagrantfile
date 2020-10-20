
Vagrant.configure("2") do |config|
    config.ssh.insert_key = false
    config.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", 1024]
        v.customize ["modifyvm", :id, "--cpus", 2]
        v.customize ["modifyvm", :id, "--name", "ansible"]
    end
      
    config.vm.define "ansible" do |centos|
        centos.vm.box = "centos/8"
		centos.vm.box_version = "1905.1"
        centos.vm.network "private_network", ip: "192.168.3.30"
		centos.vm.network "forwarded_port", guest: 80, host: 80
		centos.vm.hostname = "Ansible"
        centos.vm.provision "ansible_local" do |ansible|
         ansible.playbook = "ansible-file/playbook.yml"
            
        end
    end

    
end