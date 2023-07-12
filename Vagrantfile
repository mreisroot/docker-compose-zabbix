Vagrant.configure("2") do |config|

  # Definir provider e alocar recursos
  config.vm.provider "virtualbox" do |vb|
    vb.name = "docker-compose-zabbix"
    vb.cpus = 1
    vb.memory = 2048
    vb.gui = false
  end

  # Definir SO, hostname e rede
  config.vm.box = "almalinux/9"
  config.vm.hostname = "alma"
  config.vm.network "private_network", ip: "192.168.56.2"

  # Sincronizar pasta que contém arquivos do Ansible
  config.vm.synced_folder "ansible", "/ansible"

  # Instalar o Ansible
  config.vm.provision "shell", inline:<<-'EOF'
    dnf config-manager --set-enabled crb
    dnf install -y epel-release
    dnf install -y ansible python3-pip
  EOF

  # Provisionar a máquina pelo Ansible
  config.vm.provision "ansible_local" do |ansible|
    ansible.provisioning_path = "/ansible"
    ansible.playbook = "playbook.yml"
  end

end
