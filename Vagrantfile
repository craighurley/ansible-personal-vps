# -*- mode: ruby -*-
# vi: set ft=ruby :

# development, staging or production
environment = "development"

# ansible settings
ansible_playbook = "vps.yml"
ansible_log_level = "v"

# get details of boxes to build
boxes = YAML.load_file("boxes.yml")

Vagrant.configure(2) do |config|
  # Enable hostmanager plugin
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  boxes.each do |box|
    config.vm.define box["name"] do |box_config|
      # OS and hostname
      box_config.vm.box = box["box"]
      box_config.vm.box_version = box["box_version"]
      box_config.vm.hostname = box["name"]

      # Networking.  By default a NAT interface is added.
      # Add a internal network like this:
      #box_config.vm.network "private_network", type: "dhcp", virtualbox__intnet: true
      # Add a bridged network
      if box["public_network"]
        if box["public_network"]["ip"]
          box_config.vm.network "public_network", bridge: box["public_network"]["bridge"], ip: box["public_network"]["ip"]
        else
          box_config.vm.network "public_network", bridge: box["public_network"]["bridge"]
        end
      end

      # Shared folders
      box_config.vm.synced_folder ".", "/vagrant", disabled: true
      box_config.vm.synced_folder "./share", "/vagrant_share", create: true

      # TODO: switch provider to digital ocean
      box_config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--cpus", box["cpus"]]
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", box["cpu_execution_cap"]]
        vb.customize ["modifyvm", :id, "--memory", box["ram"]]
        vb.customize ["modifyvm", :id, "--name", box["name"]]
        vb.customize ["modifyvm", :id, "--description", box["description"]]
      end
    end
  end

  # provision boxes using ansible
  config.vm.provision :ansible do |ansible|
    ansible.playbook = ansible_playbook
    ansible.verbose = ansible_log_level
    ansible.extra_vars = {
      v_environment: environment
    }
  end
end
