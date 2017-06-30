# Defines our Vagrant environment
#
# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # create mgmt node
  config.vm.define :mgmt do |mgmt_config|
      mgmt_config.vm.box = "ubuntu/trusty64"
      mgmt_config.vm.hostname = "mgmt"
      mgmt_config.vm.network :private_network, ip: "10.0.15.10"
      mgmt_config.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
      mgmt_config.vm.provision :shell, path: "bootstrap-mgmt.sh"
  end

  # create load balancer
  config.vm.define :linux_test do |linux_test_config|
      linux_test_config.vm.box = "ubuntu/trusty64"
      linux_test_config.vm.hostname = "linux-test"
      linux_test_config.vm.network :private_network, ip: "10.0.15.11"
      #linux_test_config.vm.network "forwarded_port", guest: 80, host: 8080
      linux_test_config.vm.provider "virtualbox" do |vb|
        vb.memory = "256"
      end
  end

  config.vm.define :windows_test do |node|
      node.vm.box = "opentable/win-2012r2-standard-amd64-nocm"
      node.vm.hostname = "windows-test"
      node.vm.network :private_network, ip: "10.0.15.2"
      #node.vm.network "forwarded_port", guest: 80, host: "808#{i}"
      node.vm.network "forwarded_port", guest: 3389, host: 33389
      node.vm.provider "virtualbox" do |vb|
        vb.memory = "2048"
      end
  end

  #config.vm.define :windows_test2 do |node|
  #    node.vm.box = "opentable/win-7-professional-amd64-nocm"
  #    node.vm.hostname = "windows-test-2"
  #    node.vm.network :private_network, ip: "10.0.15.3"
      #node.vm.network "forwarded_port", guest: 80, host: "808#{i}"
  #    node.vm.network "forwarded_port", guest: 3389, host: 33389
  #    node.vm.provider "virtualbox" do |vb|
  #      vb.memory = "2048"
  #    end
  #end
end
