Vagrant.configure("2") do |config|
    config.vm.provider "virtualbox" do |v| 
    v.memory = 1024
    v.cpus = 2 
    end 
    
       #inetRouter
    config.vm.define "inetRouter" do |inetrouter|
    inetrouter.vm.box = "bento/centos-stream-8"
    inetrouter.vm.host_name = 'inetRouter'
    inetrouter.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "router-net"
    inetrouter.vm.network :private_network, adapter: 3, auto_config: false, virtualbox__intnet: "router-net"
    inetrouter.vm.network :private_network, ip: '192.168.56.10', adapter: 8
    inetrouter.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         inetrouter.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
       
       
       
       #centralRouter
    config.vm.define "centralRouter" do |centralrouter|
    centralrouter.vm.box = "bento/centos-stream-8"
    centralrouter.vm.host_name = 'centralRouter'
    centralrouter.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "router-net"
    centralrouter.vm.network :private_network, adapter: 3, auto_config: false, virtualbox__intnet: "router-net"
    centralrouter.vm.network :private_network, ip: '192.168.255.9', adapter: 6, netmask: "255.255.255.252", virtualbox__intnet: "office1-central"
    centralrouter.vm.network :private_network, ip: '192.168.56.11', adapter: 8
    centralrouter.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         centralrouter.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
    
    
    
       #office1Router
    config.vm.define "office1Router" do |office1router|
    office1router.vm.box = "bento/centos-stream-8"
    office1router.vm.host_name = 'office1Router'
    office1router.vm.network :private_network, ip: '192.168.255.10', adapter: 2, netmask: "255.255.255.252", virtualbox__intnet: "office1-central"
    office1router.vm.network :private_network, adapter: 3, auto_config: false, virtualbox__intnet: "vlan1"
    office1router.vm.network :private_network, adapter: 4, auto_config: false, virtualbox__intnet: "vlan1"
    office1router.vm.network :private_network, adapter: 5, auto_config: false, virtualbox__intnet: "vlan1"
    office1router.vm.network :private_network, adapter: 6, auto_config: false, virtualbox__intnet: "vlan1"
    office1router.vm.network :private_network, ip: '192.168.56.20', adapter: 8
    office1router.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         office1router.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
       
       
       #testClient1
    config.vm.define "testClient1" do |testclient1|
    testclient1.vm.box = "bento/centos-stream-8"
    testclient1.vm.host_name = 'testClient1'
    testclient1.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "testLAN"
    testclient1.vm.network :private_network, ip: '192.168.56.21', adapter: 8
    testclient1.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         testclient1.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
    
    
        #testServer1
    config.vm.define "testServer1" do |testserver1|
    testserver1.vm.box = "bento/centos-stream-8"
    testserver1.vm.host_name = 'testServer1'
    testserver1.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "testLAN"
    testserver1.vm.network :private_network, ip: '192.168.56.22', adapter: 8
    testserver1.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         testserver1.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
    
    
        #testClient2
    config.vm.define "testClient2" do |testclient2|
    testclient2.vm.box = "ubuntu/focal64"
    testclient2.vm.host_name = 'testClient2'
    testclient2.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "testLAN"
    testclient2.vm.network :private_network, ip: '192.168.56.31', adapter: 8
    testclient2.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         testclient2.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
    
    
        #testServer2
    config.vm.define "testServer2" do |testserver2|
    testserver2.vm.box = "ubuntu/focal64"
    testserver2.vm.host_name = 'testServer2'
    testserver2.vm.network :private_network, adapter: 2, auto_config: false, virtualbox__intnet: "testLAN"
    testserver2.vm.network :private_network, ip: '192.168.56.32', adapter: 8
    testserver2.vm.provision "shell", inline: <<-SHELL
           mkdir -p ~root/.ssh
           cp ~vagrant/.ssh/auth* ~root/.ssh
         SHELL
   
         testserver2.vm.provision "ansible" do |ansible|
             ansible.playbook = "provisioning/playbook.yml"
           ansible.inventory_path = "provisioning/hosts"
             ansible.become = "true"
         end
   
       end
    end
   
