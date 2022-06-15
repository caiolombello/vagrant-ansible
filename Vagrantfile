Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-16.04"

  config.vm.define "docker" do |docker|        
    docker.vm.hostname = "docker"
    docker.vm.network "private_network", ip: "10.10.10.10"
    docker.vm.provision :ansible do |docker_ansible|
      docker_ansible.verbose = "vv"
      docker_ansible.limit = "docker"
      docker_ansible.inventory_path = "hosts.yml"
      docker_ansible.playbook = "playbook.yml"
  end
end

  config.vm.define "db" do |db|
    db.vm.hostname = "mysql"
    db.vm.network "private_network", ip: "10.10.10.11"
    db.vm.network "forwarded_port", guest: 3306, host: 3306
    db.vm.network "forwarded_port", guest: 80, host: 8306
    db.vm.provision :ansible do |db_ansible|
      db_ansible.verbose = "vv"
      db_ansible.limit = "db"
      db_ansible.inventory_path = "hosts.yml"
      db_ansible.playbook = "playbook.yml"
    end
  end
end

