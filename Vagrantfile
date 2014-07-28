# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

ENV['VAGRANT_DEFAULT_PROVIDER'] ||= 'docker'

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.define 'postgres' do |postgres|
    postgres.vm.provider 'docker' do |d|
      d.image  = 'petergebala/docker_postgres'
      d.name   = 'example_postgres'
      d.ports  = ['5432:5432']
    end
  end

  config.vm.define 'rails' do |rails|
    rails.vm.provider 'docker' do |d|
      d.image           = 'petergebala/docker_rails'
      d.name            = 'example_rails'
      d.remains_running = false
      d.ports           = ['3000:3000']

      d.link('example_postgres:postgres')
      d.has_ssh         = true
    end

    rails.vm.synced_folder ".", "/home/deployer/app", owner: 'deployer', group: 'deployer'
  end

  config.ssh.username         = 'deployer'
  config.ssh.private_key_path = '~/.ssh/id_rsa'
  config.ssh.shell            = '/bin/zsh -l'
  config.vm.provision "shell", inline: "echo SSH works!"
end
