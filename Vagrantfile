Vagrant.configure("2") do |config|
    config.vm.box = "debian/buster64"

    config.vm.define 'medshake' do |node|
        node.vm.hostname ='medshake.local'
        node.vm.provision "ansible" do |ansible|
            ansible.playbook = "main.yml"
        end
    config.vm.network "private_network", ip: "55.55.55.5"    
    # Pour tester Dicom et Phonecapture sur son réseau local 
    #config.vm.network "public_network"   
    end
  end

