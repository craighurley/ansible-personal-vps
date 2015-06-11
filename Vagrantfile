# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  {
    :box => "puppetlabs/centos-7.0-64-puppet",
    :box_version => "1.0.1",
    :name => "vps-centos",
    :description => "Personal VPS",
    :ansible_playbook => "vps.yml",
    :ansible_log_level => "v",
    :cpus => "1",
    :cpu_execution_cap => "90",
    :ram => "1024"
  },
]

NIC = 'en0: Wi-Fi (AirPort)'
HOSTNAME_PREFIX = `hostname`.chomp.downcase[/[^.]+/]

Vagrant.configure(2) do |config|
  # Enable hostmanager plugin
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  boxes.each do |box|
    config.vm.define box[:name] do |box_config|
      # OS and hostname
      box_config.vm.box = box[:box]
      box_config.vm.box_version = box[:box_version]
      #box_config.vm.hostname = "#{HOSTNAME_PREFIX}-" + box[:name]
      box_config.vm.hostname = box[:name]

      # Networking
      # By default a NAT interface is added.  Other networks can be added as follows:
      #box_config.vm.network "private_network", type: "dhcp", virtualbox__intnet: true
      #box_config.vm.network "private_network", type: "dhcp", virtualbox__intnet: "mynetwork"
      #box_config.vm.network "public_network", bridge: NIC

      # Shared folders
      box_config.vm.synced_folder ".", "/vagrant", disabled: true
      box_config.vm.synced_folder "./share", "/vagrant_share", create: true

      # TODO: switch provider to digital ocean
      box_config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--cpus", box[:cpus]]
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", box[:cpu_execution_cap]]
        vb.customize ["modifyvm", :id, "--memory", box[:ram]]
        vb.customize ["modifyvm", :id, "--name", box[:name]]
        vb.customize ["modifyvm", :id, "--description", box[:description]]
      end

      # Configure box
      box_config.vm.provision :ansible do |ansible|
        ansible.playbook = box[:ansible_playbook]
        ansible.verbose = box[:ansible_log_level]
      end
    end
  end
end
