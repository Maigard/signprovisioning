# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  
  config.vm.define "surgeryWeb" do |box|
    box.vm.hostname = "surgeryWeb"
    box.vm.network "private_network", ip: "192.168.42.10", virtualbox__intnet: true
    box.vm.network "forwarded_port", guest: 80, host: 3002
    box.vm.box = "gusztavvargadr/iis"
    box.vm.communicator = "winrm"
    box.winrm.username = "vagrant"
    box.winrm.password = "vagrant"
    box.vm.guest = :windows 
  end

  config.vm.define "surgeryDB" do |box|
    box.vm.hostname = "surgeryDB"
    box.vm.network "private_network", ip: "192.168.42.20", virtualbox__intnet: true
    box.vm.box = "gusztavvargadr/sql-server"
    box.vm.communicator = "winrm"
    box.winrm.username = "vagrant"
    box.winrm.password = "vagrant"
    box.vm.guest = :windows 
  end

  config.vm.provision "ansible" do |ansible|
      ansible.playbook = "setupSurgery.yml"
      ansible.host_vars = {
        "surgeryWeb" => { "ansible_winrm_scheme" => "http" },
        "surgeryDB" => { "ansible_winrm_scheme" => "http" }
      }
  end

  config.vm.provider "virtualbox" do |vb|
    # Display the VirtualBox GUI when booting the machine
    vb.gui = false 
  
    # Customize the amount of memory on the VM:
    vb.memory = "2048"   
  end
end
