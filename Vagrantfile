Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/trusty64"

    # Create a forwarded port mapping which allows access to a specific port
    # within the machine from a port on the host machine. In the example below,
    # accessing "localhost:8080" will access port 80 on the guest machine.
    # config.vm.network "forwarded_port", guest: 80, host: 8080

    config.vm.network "private_network", ip: "192.168.56.20", nictype: "virtio"

    config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "4096", "--cpus", "2"]
        vb.name = "jenkins"
    end

    # Ansible provisioner.
    config.vm.provision "ansible" do |ansible|
      ansible.playbook = "provisioning/playbook.yml"
      #ansible.inventory_path = "provisioning/inventory"
      ansible.sudo = true
    end
end
