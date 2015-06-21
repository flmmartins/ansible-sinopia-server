# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.hostname = "sinopia"
  config.vm.network "forwarded_port", guest: 4873, host: 4873
  config.vm.network "forwarded_port", guest: 80, host: 80
  
  config.vm.provision "ansible" do |ansible| 
    ansible.playbook = "playbook.yml"
    ansible.verbose = '<vv></vv>'
  end
end
