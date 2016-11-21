# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = '2'

Vagrant.require_version '>= 1.5.0'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here. The most common configuration
  # options are documented and commented below. For a complete reference,
  # please see the online documentation at vagrantup.com.

  config.vm.define "development" do |development|
    development.vm.hostname = 'Chef-Nodes-Dev'
    development.vm.box = "ubuntu/trusty64"
    development.vm.network "private_network", ip: "192.168.110.11"
    config.vm.synced_folder "./etc_chef/Chef-Nodes-Dev", "/etc/chef", owner: "root", group: "root"

    if Vagrant.has_plugin?("vagrant-omnibus")
      development.omnibus.chef_version = '12.15.19'
    end
    development.berkshelf.enabled = true

    development.vm.provision :chef_solo do |chef|
      chef.run_list = [
        'recipe[chef_nodes::default]'
      ]
    end
  end

  config.vm.define "staging" do |staging|
    staging.vm.hostname = 'Chef-Nodes-Stg'
    staging.vm.box = "ubuntu/trusty64"
    staging.vm.network "private_network", ip: "192.168.110.12"
    config.vm.synced_folder "./etc_chef/Chef-Nodes-Stg", "/etc/chef", owner: "root", group: "root"

    if Vagrant.has_plugin?("vagrant-omnibus")
      staging.omnibus.chef_version = '12.15.19'
    end
    staging.berkshelf.enabled = true

    staging.vm.provision :chef_solo do |chef|
      chef.run_list = [
        'recipe[chef_nodes::default]'
      ]
    end
  end

  config.vm.define "production" do |production|
    production.vm.hostname = 'Chef-Nodes-Prod'
    production.vm.box = "ubuntu/trusty64"
    production.vm.network "private_network", ip: "192.168.110.13"
    config.vm.synced_folder "./etc_chef/Chef-Nodes-Prod", "/etc/chef", owner: "root", group: "root"

    if Vagrant.has_plugin?("vagrant-omnibus")
      production.omnibus.chef_version = '12.15.19'
    end
    production.berkshelf.enabled = true

    production.vm.provision :chef_solo do |chef|
      chef.run_list = [
        'recipe[chef_nodes::default]'
      ]
    end
  end

end
