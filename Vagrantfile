Vagrant.configure("2") do |config|
  # Define common configurations
  common_vm_config = {
    box: "ubuntu/bionic64",
    memory: "512",
    cpus: 1,
    network: "private_network",
    provision: "shell"
  }

  # Define individual VMs
  all_vms = [
    { name: "Web01", network_type: "dhcp", provision_script: "lamp.sh/" },
    { name: "Web02", network_type: "dhcp", provision_script: "lamp.sh/" },
    { name: "Db01", network_type: "dhcp", provision_script: "lamp.sh/" }
  ]

  # Choose which VMs to provision (e.g., VMs 1, 2, and 3)
  selected_vms = all_vms[0..1]

  # Loop through the selected VMs and apply configurations
  selected_vms.each do |vm|
    config.vm.define vm[:name] do |node|
      node.vm.box = common_vm_config[:box]
      node.vm.network common_vm_config[:network], type: vm[:network_type]
      node.vm.provider "virtualbox" do |vb|
        vb.memory = common_vm_config[:memory]
        vb.cpus = common_vm_config[:cpus]
      end
      node.vm.provision common_vm_config[:provision] do |provision|
        provision.path = vm[:provision_script]
      end
    end
  end
end