# -*- mode: ruby -*-
# vi: set ft=ruby :

######################################################################
# Vagrant configuratio for NYU DevOps class
######################################################################

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/bionic64"

  # forward network ports
  config.vm.network "forwarded_port", guest: 8001, host: 8001, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 8080, host: 8080, host_ip: "127.0.0.1"
  config.vm.network "forwarded_port", guest: 5000, host: 5000, host_ip: "127.0.0.1"
  # Couch DB
  config.vm.network "forwarded_port", guest: 5984, host: 5984, host_ip: "127.0.0.1"

  # add an ip address
  config.vm.network "private_network", ip: "192.168.33.10"

  # Provision a small VM when using VirtualBox
  config.vm.provider "virtualbox" do |vb|
    # Customize the amount of memory on the VM:
    vb.memory = "1024"
    vb.cpus = 2
    # Fixes some DNS issues on some networks
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end

  ######################################################################
  # Copy useful profiles from your host to your VM
  ######################################################################

  # Copy your .gitconfig file so that your git credentials are correct
  if File.exists?(File.expand_path("~/.gitconfig"))
    config.vm.provision "file", source: "~/.gitconfig", destination: "~/.gitconfig"
  end

  # Copy your ssh keys for github so that your git credentials work
  if File.exists?(File.expand_path("~/.ssh/id_rsa"))
    config.vm.provision "file", source: "~/.ssh/id_rsa", destination: "~/.ssh/id_rsa"
  end
  if File.exists?(File.expand_path("~/.ssh/id_rsa.pub"))
    config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/id_rsa.pub"
  end

  # Copy your .vimrc file so that your VI editor looks right
  if File.exists?(File.expand_path("~/.vimrc"))
    config.vm.provision "file", source: "~/.vimrc", destination: "~/.vimrc"
  end

  # Copy your IBM Clouid API Key if you have one so you can login easily
  if File.exists?(File.expand_path("~/.bluemix/apiKey.json"))
    config.vm.provision "file", source: "~/.bluemix/apiKey.json", destination: "~/.bluemix/apiKey.json"
  end

  ######################################################################
  # Provision a Python 3 development environment
  ######################################################################
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    # Python 3
    apt-get install -y git tree python3-dev python3-pip python3-venv
    apt-get -y autoremove
    sudo -H -u vagrant sh -c "echo alias a=\'. venv/bin/activate\' >> ~/.bash_aliases"
    # Make vi look nice
    # sudo -H -u vagrant echo "colorscheme desert" > ~/.vimrc
    # Install app dependencies
    # cd /vagrant
    # python3 -m venv venv
    # source venv/bin/activate
    # pip install -r requirements.txt
  SHELL

  ######################################################################
  # Add docker image before IBM Cloud
  ######################################################################
  # CouchDB Dashboard: http://127.0.0.1:5984/_utils
  config.vm.provision "docker" do |d|
    d.pull_images "couchdb"
    d.run "couchdb",
      args: "--restart=always -d --name couchdb -p 5984:5984 -v couchdb:/opt/couchdb/data -e COUCHDB_USER=admin -e COUCHDB_PASSWORD=pass"
  end

  ######################################################################
  # Setup IBM Cloud CLI and Kubernetes environment
  ######################################################################
  config.vm.provision "shell", inline: <<-SHELL
    echo "\n************************************"
    echo " Installing IBM Cloud CLI..."
    echo "************************************\n"
    # Install IBM Cloud CLI as Vagrant user
    sudo -H -u vagrant sh -c 'curl -sL http://ibm.biz/idt-installer | bash'
    sudo -H -u vagrant sh -c 'ibmcloud config --usage-stats-collect false'
    sudo -H -u vagrant sh -c "echo 'source <(kubectl completion bash)' >> ~/.bashrc"
    sudo -H -u vagrant sh -c "echo alias ic=/usr/local/bin/ibmcloud >> ~/.bash_aliases"
    echo "\n"
    echo "If you have an IBM Cloud API key in ~/.bluemix/apiKey.json"
    echo "You can login with the following command:"
    echo "\n"
    echo "ibmcloud login -a https://api.ng.bluemix.net --apikey @~/.bluemix/apiKey.json"
    echo "\n"
    echo "\n************************************"
    echo " For the Kubernetes Dashboard use:"
    echo " kubectl proxy --address='0.0.0.0'"
    echo "************************************\n"
  SHELL

end
