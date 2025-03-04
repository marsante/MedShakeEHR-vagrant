Vagrant.configure("2") do |config|
    # config.hostmanager.enabled = true
    # config.hostmanager.manage_host = true
    # config.hostmanager.manage_guest = true
    # config.hostmanager.ignore_private_ip = false
    # config.hostmanager.include_offline = true
    config.vm.box = "generic/debian12"
    config.vm.define "medshake"
    config.vm.hostname = "msehr.local"
    config.vm.network "private_network", ip: "192.168.57.4"
    config.vm.synced_folder ".", "/vagrant", type: "rsync"

    # Pour tester Phonecapture sur son réseau local 
    # config.vm.network "public_network"
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "main.yml"
    end
    # Pour personnaliser les spécifications de la machine
    config.vm.provider "libvirt" do |lb|
      lb.memory = 512
      lb.cpus = 2
    end

    config.vm.provider "qemu" do |qe|
      qe.memory = 512
      qe.cpus = 2
      # qe.qemu_dir = "/usr/local/share/qemu" # For brew user
    end

    config.vm.provider "virtualbox" do |vb|
        vb.memory = 512
        vb.cpus = 2
      end

    # Pour personnaliser sa clef ssh
    # config.ssh.insert_key = false
    # config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
    # config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    
  end

