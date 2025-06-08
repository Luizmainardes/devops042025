Vagrant.configure("2") do |config|  # Início da configuração principal do Vagrant

  config.vm.provision "shell", path: "script.sh"

  # --- VM CONTROLE ---
  config.vm.define "controle" do |controle|
    controle.vm.box = "shekeriev/debian-11"
    controle.vm.hostname = "controle-server"
    controle.vm.network "private_network", ip: "172.17.177.100"

    # Configuração do VirtualBox para a VM "controle"
    controle.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.cpus = 2
      vb.name = "controle"
    end

    # Mapeamento de pasta compartilhada com o host
    controle.vm.synced_folder ".", "/vagrant", type: "virtualbox"

    # Provisionamento via Ansible Local
    controle.vm.provision "ansible_local" do |al|
      al.playbook = "/vagrant/principal.yml"
      al.install_mode = "pip"
    end
  end

  # --- VM WEB ---
  config.vm.define "web" do |web|
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "web-server"
    web.vm.network "private_network", ip: "172.17.177.101"

    # Configuração do VirtualBox para a VM "web"
    web.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "web"
    end
  end

  # --- VM DB ---
  config.vm.define "db" do |db|
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "db-server"
    db.vm.network "private_network", ip: "172.17.177.102"

    # Configuração do VirtualBox para a VM "db"
    db.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 2
      vb.name = "db"
    end
  end

end  # Fim da configuração principal do Vagrant
