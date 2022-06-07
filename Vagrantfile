# -*- mode: ruby -*- # vi: set ft=ruby :
Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.ssh.insert_key = false
  config.vm.synced_folder '.', '/vagrant', disabled: true
  # General VirtualBox VM configuration.
  config.vm.provider :virtualbox do |v|
    v.memory = 1024
    v.cpus = 1
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # ubuntu.
  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.hostname = "presentations"
    ubuntu.vm.network :private_network, ip: "192.168.2.100"
    config.vm.box = "geerlingguy/ubuntu1804"
    config.ssh.insert_key = false
    ubuntu.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 8196]
      v.customize ["modifyvm", :id, "--cpus", 2]
      v.customize ["modifyvm", :id, "--vram", 128]
      v.customize ["modifyvm", :id, "--accelerate3d", "off"]
    end
  config.vm.synced_folder ".", "/vagrant", type: "rsync",
    rsync__exclude: ".git/"
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
  end
  end
end