# -*- mode: ruby -*-
# vi: set ft=ruby :

# require_relative 'lib/proxy.rb'

Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-16.04"

  config.vm.provider "virtualbox" do |vb|
    # vb.gui = true
    # vb.name = "xenial"
    vb.memory = "4096"
    # vb.cpus = 2
  end
  
  config.vm.provision "chef_client", run: :always do |chef|

    # cookbook_path            ["#{current_dir}/../cookbooks"]

    chef.node_name = "capnregex"

    chef.chef_server_url = "https://api.chef.io/organizations/userhackable"

    chef.validation_client_name = 'userhackable-validator'
    chef.validation_key_path = "/home/rob/.chef/userhackable-validator.pem"

    # chef.client_key_path = "/home/rob/.chef/capnregex.pem"
    # chef.validation_key_path = "validation.pem"

    chef.product = 'chefdk'

#    chef.http_proxy = proxy.http
#    chef.https_proxy = proxy.https
#    chef.no_proxy = proxy.no
#    chef.json = { proxy: proxy.to_h }

    #chef.add_recipe "proxy"
    chef.add_recipe "ubuntu"
    #chef.add_recipe "update"
    #chef.add_recipe "xubuntu"
    #chef.add_recipe "xubuntu::start"

    # cleanup server
    chef.delete_node = true
    chef.delete_client = true
  end
end
