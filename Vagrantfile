# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Centos 6.4
  config.vm.box = "centos"

  # Debian 7.0rc1
  #config.vm.box = "debian-70rc1-x64-vbox4210-nocm"
  #config.vm.box_url = "https://s3-ap-southeast-2.amazonaws.com/dhall-ansible-dojo/debian-70rc1-x64-vbox4210-nocm.box"

  # Ubuntu 12.04.2
  #config.vm.box = "ubuntu-server-12042-x64-vbox4210-nocm"
  #config.vm.box_url = "https://s3-ap-southeast-2.amazonaws.com/dhall-ansible-dojo/ubuntu-server-12042-x64-vbox4210-nocm.box"

  # We plan to setup a webserver
  config.vm.network :private_network, ip: "192.168.33.10"
  config.vm.network :forwarded_port, guest: 80, host: 8080

  # Configure with Ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "default.yml"
    ansible.sudo = true
    ansible.host_key_checking = false
  end 

end
