# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "precise64"
    config.vm.network "private_network", ip: "192.168.33.10"
    config.ssh.forward_agent = true
    config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--memory", "1024"]
        vb.customize ["modifyvm", :id, "--cpus", 2]
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", 100]
    end

    $script = <<SCRIPT
        if [ ! -f /usr/bin/php ] && [ ! -f /usr/bin/vim ]; then
            echo "Provisioning..."
            apt-get update
            apt-get install -y -qq vim php5-cli
            echo "I'm done :)"
        fi
SCRIPT

    config.vm.provision "shell", inline: $script
end
