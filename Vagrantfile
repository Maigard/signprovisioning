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

  
  config.vm.define "surgeryWeb" do |box|
    box.vm.synced_folder "vbsrc", "/vbsrc"
    box.vm.network "private_network", ip: "192.168.42.10"
    box.vm.network "forwarded_port", guest: 80, host: 8080
    box.vm.box = "gusztavvargadr/iis"
    box.vm.communicator = "winrm"
    box.winrm.username = "vagrant"
    box.winrm.password = "vagrant"
    box.vm.guest = :windows 
    box.vm.disk :disk, size: "10GB", name: "surgery_website"
  end

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "setupSurgery.yml"
      ansible.host_vars = {
        "surgeryWeb" => { "ansible_winrm_scheme" => "http" }
      }
  end

  # Provider-specific configuration so you can fine-tune various
  # backing providers for Vagrant. These expose provider-specific options.
  # Example for VirtualBox:
  #
  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false 
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"   
  end

  # View the documentation for the provider you are using for more
  # information on available options.
  
end
