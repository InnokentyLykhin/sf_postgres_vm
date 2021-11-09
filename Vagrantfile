# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.define "sf__legacy_vagrant"
  config.vm.box = "ubuntu/bionic64"
  config.vm.synced_folder "O:\\vagrantvm\\sf_postgres_vm", "/home/vagrant/test"
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
  end

  config.ssh.shell = "bash -c 'BASH_ENV=/etc/profile exec bash'"
  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get -y update
    sudo apt-get install -y python3 python3-pip libpq-dev
	sudo pip3 install  psycopg2
	sudo pip3 install django
	sudo apt-get install -y git-core curl zlib1g-dev build-essential 
    sudo apt-get install -y libssl-dev libreadline-dev libyaml-dev 
    sudo apt-get install -y libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev 
    sudo apt-get install -y libcurl4-openssl-dev libffi-dev
	
	# Import the repository signing key:
    
	wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
    
	# Update the package lists:
    sudo apt-get update
    
	# Install the latest version of PostgreSQL.
    # If you want a specific version, use 'postgresql-12' or similar instead of 'postgresql':
    #sudo apt-get -y remove postgresql
	
	sudo apt-get -y install 'postgresql-8.4'
    SHELL
end 
