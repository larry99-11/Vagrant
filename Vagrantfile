Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/bionic64"
    config.vm.hostname = "VagrantHost1"
    config.vm.network "private_network", ip: "172.16.1.5"
    config.vm.synced_folder "data/", "/home/vagrant/data"
    config.vm.provision "file", source: "pringle_flavours.txt", destination: "/home/vagrant/pringle_flavours.txt"

    # configuring VM resources
    config.vm.provider "virtualbox" do |vb|
      vb.customize ["modifyvm", :id, "--memory", 1024]
      vb.customize ["modifyvm", :id, "--cpus", 2]
    end 
  end
