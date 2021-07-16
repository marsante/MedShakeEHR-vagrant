Vagrant.configure("2") do |config|
    config.vm.box = "debian/bullseye64"

    # Pour personnaliser sa clef ssh
    #config.ssh.insert_key = false
    #config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
    #config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    
    #Pour personnaliser les spécifications de la machine
    #config.vm.provider "virtualbox" do |v|
    #    v.memory = 512
    #    v.cpus = 2
    #  end
    config.vm.define 'medshake' do |node|
        node.vm.hostname ='msehr.local'
        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "main.yml"
        end
    config.vm.network "private_network", ip: "55.55.55.5"    
    # Pour tester Phonecapture sur son réseau local 
    #config.vm.network "public_network"   
    end
  end

