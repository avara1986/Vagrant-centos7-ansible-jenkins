# -*- mode: ruby -*-
# vi: set ft=ruby :

# ##############################################################
# Run Tuenti with Vagrant
# ##############################################################
Vagrant.configure(2) do |config|
  config.vm.define "web" do |web|
    web.vm.box = "centos/7"

    web.vm.network "private_network", ip: "192.168.100.3"

    web.vm.provision "ansible" do |ansible|
      ansible.extra_vars = { ansible_ssh_user: 'vagrant' }

      ansible.playbook = "site.yml"
      ansible.limit = 'dbservers'
      ansible.inventory_path = "hosts"
      ansible.host_key_checking = false
    end
  end
end