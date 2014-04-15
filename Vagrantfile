# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "parallels/ubuntu-13.10"

  config.vm.network "public_network"

  config.vm.synced_folder ".", "/workspace"
  
  config.vm.provision "docker"
	
  config.vm.provision "docker" do |d|
    d.run "gsogol/docker-elk",
      auto_assign_name: false, 
      args: "-v '/workspace:/workspace' -p 80:80 -p 9200:9200 -p 49021:49021 -p 49022:49022 -p 122:22 -p 9999:9999/udp"
  end
end
