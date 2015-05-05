# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes = [
  {
    :box => "ubuntu/trusty64",
    :box_version => "20150427.0.0",
    :name => "vps",
    :description => "Personal VPS",
    :playbook => "vps.yml",
    :cpus => "2",
    :cpu_execution_cap => "66",
    :ram => "1024"
   },
]

NIC = 'en0: Wi-Fi (AirPort)'
HOSTNAME_PREFIX = `hostname`.chomp.downcase[/[^.]+/]

Vagrant.configure(2) do |config|
  boxes.each do |box|
    config.vm.define box[:name] do |vps_config|
      config.vm.box = box[:box]
      config.vm.box_version = box[:box_version]

      hostname = "#{HOSTNAME_PREFIX}-" + box[:name]
      vps_config.vm.hostname = hostname
      vps_config.vm.network "public_network", bridge: NIC

      # TODO: switch provider to digital ocean
      config.vm.provider "virtualbox" do |vb|
        vb.customize ["modifyvm", :id, "--cpus", box[:cpus]]
        vb.customize ["modifyvm", :id, "--cpuexecutioncap", box[:cpu_execution_cap]]
        vb.customize ["modifyvm", :id, "--memory", box[:ram]]
        vb.customize ["modifyvm", :id, "--name", box[:name]]
        vb.customize ["modifyvm", :id, "--description", box[:description]]
      end

      vps_config.vm.provision :ansible do |ansible|
        ansible.playbook = "ansible/" + box[:playbook]
        ansible.verbose = "vvvv"
      end
    end
  end
end
