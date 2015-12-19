Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty32"

  config.vm.network "private_network", ip: "192.168.33.204"

  # Provision
  config.vm.provision "shell", inline: "sudo ln -s /vagrant/vendor/adamnicholson/server01 /root/provision"
  config.vm.provision "shell", inline: "sudo /vagrant/vendor/adamnicholson/server01/provision/install_services.sh"

  # Deploy
  config.vm.provision "shell", inline: "sudo rm -R /opt/000-default.com"
  config.vm.provision "shell", inline: "sudo mkdir /opt/maxnicholson.co.uk"
  config.vm.provision "shell", inline: "sudo ln -s /vagrant /opt/maxnicholson.co.uk/current"
  config.vm.provision "shell", inline: "sudo ln -s /opt/maxnicholson.co.uk/current/nginx.conf /opt/maxnicholson.co.uk/nginx.conf"
  config.vm.provision "shell", inline: "sudo service nginx reload"

  config.vm.provider "virtualbox" do |v|
    v.memory = 512
    v.cpus = 1
  end
end
