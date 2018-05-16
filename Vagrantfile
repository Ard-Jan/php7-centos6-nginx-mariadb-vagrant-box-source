# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

ANSIBLE_PATH = "provision"

Vagrant.configure(2) do |config|
  # Disable default virtual box shared folder
  config.vm.synced_folder ".", "/vagrant", disabled: true

  # Which centos box should be used? #https://app.vagrantup.com/centos/boxes/6
  config.vm.box = "centos/6"
  config.vm.box_version = ">= 1803.01"

  # The name of the box cannot be to long, because this will give problems on windows
  config.vm.provider :virtualbox do |vb|
    vb.name = "php7-MariaDB-nginx-Centos6"
  end

  # Execute the ansible versions
  config.vm.provision :ansible do |ansible|
    ansible.playbook = File.join(ANSIBLE_PATH, "playbook.yml")
    ansible.verbose = true
  end
end

