Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/trusty64"
    # config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    config.vm.hostname = "nodejs-mongodb"
    
    config.vbguest.auto_update = true
    
    # Forward Oracle port
    config.vm.network :forwarded_port, guest: 1521, host: 1521
    
    # providers for Vagrant. These expose provider-specific options.
    config.vm.provider :virtualbox do |vb|
        # Use VBoxManage to customize the VM
        vb.customize ["modifyvm", :id,
                                    # RAM Memory
                                    "--memory", "512",
                                    # CPU core number
                                    "--cpus", "1",
                                    # Enable DNS behind NAT
                                    "--natdnshostresolver1", "on"]
    end

    #config.vm.provider :virtualbox do |vb|
    #    vb.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
    #    vb.customize ["modifyvm", :id, "--memory", "512"]
    #end
    
    config.vm.provision :shell, :path => "node-bootstrap.sh"
    
end
