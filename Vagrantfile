Vagrant.configure(2) do |config|
  config.vm.box = "hfm4/centos7"

  config.vm.hostname = "php7-lamp"
  config.vm.network "private_network", ip: "192.168.33.10"

  config.vm.synced_folder "./www", "/vagrant", create: true, owner: 'vagrant', group: 'vagrant', mount_options: ['dmode=777','fmode=755']

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  # Ansible provisioner.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/playbook.yml"
    ansible.inventory_path = "provisioning/inventory"
    ansible.extra_vars = "@provisioning/project_vars.yml"
    ansible.sudo = true
    ansible.limit = 'all'
  end
end
