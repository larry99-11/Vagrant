Vagrant.configure("2") do |config|
  servers=[
      {
        :hostname => "Server1",
        :box => "ubuntu/bionic64",
        :ip => "172.16.1.5",
        :ssh_port => '2200'
      },
      {
        :hostname => "Server2",
        :box => "ubuntu/bionic64",
        :ip => "172.16.1.6",
        :ssh_port => '2201'
      },
      {
        :hostname => "Server3",
        :box => "ubuntu/bionic64",
        :ip => "172.16.1.7",
        :ssh_port => '2202'
      }
    ]

  servers.each do |machine|
      config.vm.define machine[:hostname] do |node|
          node.vm.box = machine[:box]
          node.vm.hostname = machine[:hostname]
          node.vm.network :private_network, ip: machine[:ip]
          node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"
          node.vm.synced_folder "data/", "/home/vagrant/data"
          node.vm.provision "file", source: "pringle_flavours.txt", destination: "/home/vagrant/pringle_flavours.txt"
  
        # configuring VM resources
          node.vm.provider :virtualbox do |vb|
              vb.customize ["modifyvm", :id, "--memory", 512]
              vb.customize ["modifyvm", :id, "--cpus", 1]
          end
      end
  end
end