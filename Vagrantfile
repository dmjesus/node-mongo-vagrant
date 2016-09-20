Vagrant.configure("2") do |config|
    config.vm.box = "precise64"
    config.vm.box_url = "http://files.vagrantup.com/precise64.box"
    
    config.vm.hostname = "oracle"
    # config.vm.network :private_network, ip: '10.0.33.34'
    
    # Forward Oracle port
    config.vm.network :forwarded_port, guest: 1521, host: 1521
    
    config.vm.provider :virtualbox do |vb|
        vb.customize ["setextradata", :id,
                  "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1",
                  # RAM Memory
                  "--memory", "1024",
                  # CPU core number
                  "--cpus", "1",
                  # Enable DNS behind NAT
                  "--natdnshostresolver1", "on"]
    end
    
    config.vm.provision :shell, :path => "node-bootstrap.sh"
end
