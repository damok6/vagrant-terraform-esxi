# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/bionic64"

  # Create a public network, which generally matched to bridged network.
  # Bridged networks make the machine appear as another physical device on
  # your network.
  # config.vm.network "public_network"

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
	sudo apt-get install unzip golang-go -y
	wget https://releases.hashicorp.com/terraform/0.11.10/terraform_0.11.10_linux_amd64.zip
	unzip terraform_0.11.10_linux_amd64.zip
	sudo mv terraform /usr/local/bin/

	# Install ovftool
	# Alternative to getting your own ovftool, but it is older:
	#wget -m http://ftp.tucha13.net/pub/software/VMware-ovftool-4.1.0/VMware-ovftool-4.1.0-2459827-lin.x86_64.bundle -O ovftool.bundle
	#sudo sh ovftool.bundle --eulas-agreed
	# Download the new version here:
	# https://www.vmware.com/support/developer/ovf/
	sudo sh /vagrant/VMware-ovftool-4.3.0-7948156-lin.x86_64.bundle --eulas-agreed

	export GOPATH="/usr/local/lib"
	go get -u golang.org/x/crypto/ssh

	mkdir -p $GOPATH/src/github.com/hashicorp
	cd $GOPATH/src/github.com/hashicorp
	git clone https://github.com/hashicorp/terraform.git

	mkdir -p $GOPATH/src/github.com/terraform-providers
	cd $GOPATH/src/github.com/terraform-providers
	git clone https://github.com/josenk/terraform-provider-esxi.git

	cd $GOPATH/src/github.com/terraform-providers/terraform-provider-esxi
	go build -o terraform-provider-esxi_`cat version`

	cp terraform-provider-esxi_`cat version` /usr/local/bin
	
  SHELL
end
