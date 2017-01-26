# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/xenial64'
  config.vm.network "forwarded_port", guest: 4567, host: 4567

  $script = <<-SCRIPT
    echo Instalando o Docker;
    cd /vagrant;
    if ! type "docker" > /dev/null; then
      chmod o+x scripts/install-docker.sh;
      sh scripts/install-docker.sh;
    fi;
    docker-compose build;
    docker-compose up;
  SCRIPT
  config.vm.provision "shell", inline: $script, privileged: false
end
