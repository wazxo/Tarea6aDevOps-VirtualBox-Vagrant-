Vagrant.configure("2") do |config|
  # Configuración de la primera máquina virtual
  config.vm.define "web1" do |web1|
    web1.vm.box = "ubuntu/jammy64"
    web1.vm.hostname = "web1"
    web1.vm.network "private_network", ip: "192.168.33.10"

    web1.vm.synced_folder "./Pagina", "/var/www/html", type: "virtualbox"
    
    web1.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end

    web1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      systemctl enable apache2
      systemctl start apache2
    SHELL
  end

  # Configuración de la segunda máquina virtual
  config.vm.define "web2" do |web2|
    web2.vm.box = "ubuntu/jammy64"
    web2.vm.hostname = "web2"
    web2.vm.network "private_network", ip: "vagrant ssh web2"

    web2.vm.synced_folder "./Pagina", "/var/www/html", type: "virtualbox"
    
    web2.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end

    web2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      systemctl enable apache2
      systemctl start apache2
    SHELL
  end
end
