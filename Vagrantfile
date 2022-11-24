# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
 config.vm.box = "ubuntu/jammy64"
 config.vm.network "public_network", bridge: "wlp3s0"
 config.vm.box_check_update = false

  config.vm.define "app" do |app|
    app.vm.box = "ubuntu/jammy64"
    app.vm.hostname = "app"
    app.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/docker.yml"
  end
  end

  config.vm.define "mon" do |mon|
    mon.vm.box = "ubuntu/jammy64"
    mon.vm.hostname = "monitoring"
    mon.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/grafana.yml"
  end
 end

end
