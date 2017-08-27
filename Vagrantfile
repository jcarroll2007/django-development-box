# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "django-dev-box"
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"
  config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"

  config.ssh.insert_key = false
  # config.ssh.private_key_path = File.join(File.expand_path(File.dirname(__FILE__)), "provision/keys/id_rsa")

  config.vm.provision "shell", path: "./provision/scripts/install_ansible.sh"

  # Run Ansible from the Vagrant VM
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "./provision/playbook.yml"
    ansible.verbose = true
  end
end
