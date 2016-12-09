# -*- mode: ruby -*-
# vi: set ft=ruby :

# Stuff for development that we dont want to have in ansible playbook
$script = <<SCRIPT
	rpm -e vim-minimal --nodeps
    dnf install -y python-ipdb vim
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.box = "fedora/25-cloud-base"

  config.vm.network "private_network", ip: "192.168.242.65"
  config.vm.network "forwarded_port", guest: 5000, host: 5000

  config.vm.provision "shell", inline: $script
  config.vm.provision :ansible do |ansible|
    ansible.playbook = "copr-mbs.yml"
	ansible.verbose = "v"
  end
end
