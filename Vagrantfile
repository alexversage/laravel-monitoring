# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
 config.vm.box = "ubuntu/jammy64"
 config.vm.network "public_network", bridge: "wlp3s0"
# use_dhcp_assigned_default_route: true

  config.vm.define "app" do |app|
    app.vm.box = "ubuntu/jammy64"
    app.vm.hostname = "app"
  end

  config.vm.define "monitoring" do |monitoring|
    monitoring.vm.box = "ubuntu/jammy64"
    monitoring.vm.hostname = "monitoring"
  end

  config.vm.define "ans" do |ans|
  ans.vm.box = "ubuntu/jammy64"
  ans.vm.hostname = "ans"
  ans.vm.provision :shell, :inline  => "
        sudo apt-get -y update;
        sudo apt install -y software-properties-common;
        sudo apt-add-repository --yes --update ppa:ansible/ansible;
        sudo apt install -y ansible;
        touch /etc/ansible/playbook.yml     "
  ans.vm.provision :ansible_local do |ansible|
    ansible.playbook = "/etc/ansible/playbook.yml"
  end
end
end
