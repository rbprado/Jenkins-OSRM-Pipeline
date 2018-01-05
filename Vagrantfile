Vagrant.configure('2') do |config|

  config.vm.define 'jenkins-sentiance' do |config|

    config.vm.provider :digital_ocean do |provider, override|
	  override.ssh.private_key_path = '~/.ssh/id_rsa'
	  override.vm.box = 'digital_ocean'
	  override.vm.box_url = "https://github.com/smdahlen/vagrant-digitalocean/raw/master/box/digital_ocean.box"
      provider.token = ENV["DO_TOKEN"]
      provider.image = 'ubuntu-14-04-x64'
      provider.region = 'nyc3'
      provider.size = '1GB'
      provider.ssh_key_name = 'Ubuntu Casa'
    end

    config.vm.provision :ansible do |ansible|
      ansible.playbook            = 'jenkins.yml'
      ansible.verbose             = 'v'
      ansible.host_key_checking   = false
      ansible.limit               = 'all'
    end

  end
end
