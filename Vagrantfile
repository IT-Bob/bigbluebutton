# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"

  # machine configuration
  config.vm.network "forwarded_port", guest: 22, host: 2222
  # disable synced folder
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.disk :disk, size: "60GB"
  config.vm.provider "virtualbox" do |v|
    v.memory = 8192
    v.cpus = 4
  end

  # use the default Vagrant insure key
  config.ssh.insert_key = false

  # ensure that system locales are en_US.UTF-8
  $locale = <<-SCRIPT
    sudo apt-get install -y language-pack-en \
      && sudo update-locale LANG=en_US.UTF-8
  SCRIPT

  config.vm.provision "shell", inline: $locale
end
