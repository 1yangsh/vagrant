Vagrant.configure("2") do |config|
  # Node1
  config.vm.define:"node-1" do |cfg|
    cfg.vm.box = "centos/7"
    cfg.vm.provider:virtualbox do |vb|
        vb.name="node-1"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 1024]
    end
    cfg.vm.host_name="node1"
    # cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
    cfg.vm.network "private_network", ip: "192.168.56.11"
    cfg.vm.network "forwarded_port", guest: 22, host: 19211, auto_correct: false, id: "ssh"
    cfg.vm.network "forwarded_port", guest: 8080, host: 18080
    cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end

  # Node2
  config.vm.define:"node-2" do |cfg|
    cfg.vm.box = "centos/7"
    cfg.vm.provider:virtualbox do |vb|
        vb.name="node-2"
        vb.customize ["modifyvm", :id, "--cpus", 1]
        vb.customize ["modifyvm", :id, "--memory", 1024]
    end
    cfg.vm.host_name="node2"
    # cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
    cfg.vm.network "private_network", ip: "192.168.56.12"
    cfg.vm.network "forwarded_port", guest: 22, host: 19212, auto_correct: false, id: "ssh"
    cfg.vm.network "forwarded_port", guest: 8080, host: 28080
    cfg.vm.network "forwarded_port", guest: 30234, host: 30234 
    cfg.vm.provision "shell", path: "bash_ssh_conf_4_CentOS.sh"
  end

  # master
  config.vm.define:"master" do |cfg|
    cfg.vm.box = "centos/7"
    cfg.vm.provider:virtualbox do |vb|
        vb.name="master"
        vb.customize ["modifyvm", :id, "--cpus", 2]
        vb.customize ["modifyvm", :id, "--memory", 2048]
    end
    cfg.vm.host_name="master"
    # cfg.vm.synced_folder ".", "/vagrant", type: "nfs"
    cfg.vm.network "private_network", ip: "192.168.56.10"
    cfg.vm.network "forwarded_port", guest: 22, host: 19214, auto_correct: false, id: "ssh"
    cfg.vm.network "forwarded_port", guest: 8080, host: 48080
    cfg.vm.network "forwarded_port", guest: 8001, host: 48001
    
  end
end