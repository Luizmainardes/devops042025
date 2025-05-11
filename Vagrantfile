Vagrant.configure("2") do |config|     # <== INÍCIO do bloco principal do Vagrant
  config.vm.provision "shell", path: "script.sh"

  config.vm.define "controle" do |controle|      # <== INÍCIO da definição da VM "controle"
    controle.vm.box = "shekeriev/debian-11"
    controle.vm.hostname = "controle-server"
    controle.vm.network "private_network", ip: "172.17.177.100"
    controle.vm.provider "virtualbox" do |vb|  # <== INÍCIO do bloco de configuração do VirtualBox pra VM "controle"
      vb.memory = "2048"
      vb.cpus = 2
      vb.name = "controle"
    end                                # <== FIM do bloco VirtualBox da VM "controle"
    controle.vm.provision "ansible_local" do |al|
      al.playbook = "playbook.yml"
      al.install_mode = "pip"
    end                                # <== FIM do bloco ansible VM "controle"
  end                                  # <== FIM da definição da VM "controle"

  config.vm.define "web" do |web|      # <== INÍCIO da definição da VM "web"
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "web-server"
    web.vm.network "private_network", ip: "172.17.177.101"
    web.vm.provider "virtualbox" do |vb|  # <== INÍCIO do bloco de configuração do VirtualBox pra VM "web"
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "web"
    end                                # <== FIM do bloco VirtualBox da VM "web"
  end                                  # <== FIM da definição da VM "web"

  config.vm.define "db" do |db|        # <== INÍCIO da definição da VM "db"
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "db-server"
    db.vm.network "private_network", ip: "172.17.177.102"
    db.vm.provider "virtualbox" do |vb|  # <== INÍCIO do bloco de configuração do VirtualBox pra VM "db"
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "db"
    end                                # <== FIM do bloco VirtualBox da VM "db"
  end                                  # <== FIM da definição da VM "db"

end                                    # <== FIM do bloco principal do Vagrant
