# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "parallels/ubuntu-13.10"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder ".", "/workspace"
  
  config.vm.provision "docker"
	
  # Provision docker
  cmd = <<SCRIPT
  docker build -t gsogol/elk /workspace/.
SCRIPT
 
  config.vm.provision :shell, :inline => cmd
 
  config.vm.provision "docker" do |d|
    d.run "gsogol/elk", 
      args: "-v '/workspace:/workspace' -p 80:8080 -p 9200:9200 -p 49021:49021"
  end
end
