Vagrant.configure("2") do |config|
  config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/me.pub"
  (2..3).each do |i|
    NODE_NUMBER = i - 1
    config.vm.define "node0#{NODE_NUMBER}" do |node|
      node.vm.provision "shell", inline: <<-SHELL
        cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
      SHELL
      node.vm.box = "generic/ubuntu2004"
      node.vm.network "private_network", ip: "192.168.62.#{i}"
    end
  end
end
