Vagrant.configure("2") do |config|
    config.vm.box = "ubuntu/focal64"
  
    config.vm.define "manager" do |manager|
      manager.vm.hostname = "manager"
      manager.vm.network "private_network", ip: "192.168.56.10"
      manager.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
        sudo apt-get update
        sudo apt-get install -y docker-ce docker-ce-cli containerd.io
      SHELL
    end
  
    config.vm.define "worker1" do |worker|
      worker.vm.hostname = "worker1"
      worker.vm.network "private_network", ip: "192.168.56.11"
      worker.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
        sudo apt-get update
        sudo apt-get install -y docker-ce docker-ce-cli containerd.io
      SHELL
    end
  
    config.vm.define "worker2" do |worker|
      worker.vm.hostname = "worker2"
      worker.vm.network "private_network", ip: "192.168.56.12"
      worker.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
        curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
        sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable"
        sudo apt-get update
        sudo apt-get install -y docker-ce docker-ce-cli containerd.io
      SHELL
    end
  end
  