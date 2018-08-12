# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.

# Setting up the default box provider
ENV['VAGRANT_DEFAULT_PROVIDER'] = 'virtualbox'

# SCRIPT to install Services on the vm.box
# sample script to install appache service on the box
$samplescript = <<SCRIPT
	yum install -y httpd
	systemctl enable httpd
	systemctl start httpd
SCRIPT

# starting vm.boxes configuration

# base vm.box config
#  Vagrant.configure(2) do |config|
#	config.vm.box = "base"
#  end

Vagrant.configure("2") do |config|

# base guide line for configuring vm.box 
# ----------------------------------------------------------------------

  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://vagrantcloud.com/search.
  # config.vm.box = "base"

  # Disable automatic box update checking. If you disable this, then
  # boxes will only be checked for updates when the user runs
  # `vagrant box outdated`. This is not recommended.
  # config.vm.box_check_update = false

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. In the example below,
  # accessing "localhost:8080" will access port 80 on the guest machine.
  # NOTE: This will enable public access to the opened port
  # config.vm.network "forwarded_port", guest: 80, host: 8080

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine and only allow access
  # via 127.0.0.1 to disable public access
  # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  # config.vm.network "private_network", ip: "192.168.33.10"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../data", "/vagrant_data"

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  # View the documentation for the provider you are using for more
  # information on available options.

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  # config.vm.provision "shell", inline: <<-SHELL
  #   apt-get update
  #   apt-get install -y apache2
  # SHELL

# ----------------------------------------------------------------------

	# Customize the VirtualBox vm.box srv1 <<
	#
	# >>>> default config: 1 cpu + 500 MB memory
	# >> Global config for all vm.boxes
	#
	config.vm.provider "virtualbox" do |vb|
		vb.gui = false
		vb.linked_clone = true
		vb.memory = "2048"
		vb.cpus	= "2"
	end

	# this is the default (primary) machine !!
	config.vm.define "srv1", primary: true do |srv1|
		srv1.vm.box = "centos/7"
		srv1.vm.hostname = "vagcentos7"	
	
		# a private network ip address
		# srv1.vm.network "private_network", ip: "192.168.50.10"
	
		# srv1.vm.synced_folder "src/", "/var/www/html"
	
		# SCRIPT installing Service
		# srv1.vm.provision "shell", inline: $samplescript
	
		srv1.vm.post_up_message = "vm.box centos/7 as vagcentos7 is setup!"
	end
	
	# Customize the VirtualBox vm.box srv1 <<
	#
	config.vm.define "srv2" do |srv2|
		srv2.vm.box = "ubuntu/trusty64"
		srv2.vm.hostname = "vagubuntusrv1"	
		srv2.vm.post_up_message = "vm.box ubuntu/trusty64 as vagubuntu_srv1 is setup!"
	end
  	
end
