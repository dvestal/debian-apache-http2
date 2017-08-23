# -*- mode: ruby -*-
# vi: set ft=ruby :

digital_ocean_token = File.open(File.expand_path('~/.config/digital_ocean.token'), 'rb') { |f| f.read }

Vagrant.configure('2') do |config|
  config.vm.box = 'dummy'
  config.ssh.private_key_path = '~/.ssh/id_rsa'

  config.vm.provider :digital_ocean do |provider, override|
    provider.token = digital_ocean_token
    provider.image = 'debian-9-x64'
    provider.region = 'fra1'

    override.vm.box = 'digital_ocean'
    override.vm.box_url = 'https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box'
  end

  config.vm.provision :ansible do |ansible|
    ansible.playbook = 'playbook.yml'
  end
end
