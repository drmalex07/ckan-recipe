# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

inventory_file = ENV['INVENTORY_FILE'] || 'hosts.yml'

inventory = YAML.load_file(inventory_file)
inventory_vars = inventory['all']['vars']
inventory_groups = inventory['all']['children']


Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.box_check_update = false

  config.vm.synced_folder "./vagrant-data/", "/vagrant", type: "rsync"

  config.vm.define "ckan" do |ckan|
    h = inventory_groups['ckan']['hosts']['ckan']
    ckan.vm.network "private_network", ip: h['ipv4_address'] 
    ckan.vm.provider "virtualbox" do |vb|
      vb.name = h['fqdn']
      vb.memory = 1024
    end
  end

  # Provision (common)
  
  config.vm.provision "file", source: "keys/id_rsa", destination: ".ssh/id_rsa"
  config.vm.provision "shell", path: "scripts/copy-key.sh", privileged: false

  config.vm.provision "file", source: "files/profile", destination: ".profile"
  config.vm.provision "file", source: "files/bashrc", destination: ".bashrc"
  config.vm.provision "file", source: "files/vimrc", destination: ".vimrc"

  config.vm.provision "shell", inline: <<-EOD
    apt-get update && apt-get install -y sudo python
  EOD
 
end
