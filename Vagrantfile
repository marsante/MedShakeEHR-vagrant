Vagrant.configure("2") do |config|
    config.vm.box = "debian/bullseye64"

    # Pour personnaliser sa clef ssh
    #config.ssh.insert_key = false
    #config.ssh.private_key_path = ["~/.ssh/id_rsa", "~/.vagrant.d/insecure_private_key"]
    #config.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
    
    #Pour personnaliser les spécifications de la machine
    # config.vm.provider "virtualbox" do |v|
    #     v.memory = 1024
    #     v.cpus = 4
    #   end
    config.vm.define 'medshake' do |node|
        node.vm.hostname ='msehr.local'
        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "main.yml"
        end
    config.vm.network "private_network", ip: "192.168.56.4"    
    # Pour tester Phonecapture sur son réseau local 
    #config.vm.network "public_network"   
    end
  end

