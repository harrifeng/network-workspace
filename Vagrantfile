Vagrant.configure("2") do |config|

  $num_instances = 2

  (1..$num_instances).each do |i|

    config.vm.define "ubuntu-#{i}" do |app|
      app.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "1024"
        vb.cpus = 1
      end
      app.vm.hostname = "ubuntu-#{i}"
      app.vm.box = "bento/ubuntu-18.04"
      app.vm.box_check_update = false
      app.ssh.insert_key = false
      app.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key']
      app.vm.network "private_network", ip: "10.19.19.6#{i}"
      app.vm.network "public_network"
      app.vm.provision "shell", path: "prepare.sh"
    end
  end
end
