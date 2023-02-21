IMAGE_NAME = "ubuntu/focal64"

MASTER_MEMORY=3072

NETWORK_PREFIX="192.168.165"

Vagrant.configure("2") do |config|

    config.vm.define "minikube-dev-ca" do |master|
        master.vm.box = IMAGE_NAME
        master.vm.network "private_network", ip: "#{NETWORK_PREFIX}.10"
        master.vm.hostname = "minikube-dev-ca"
        master.vm.provider :virtualbox do |vb|
            vb.name = "minikube-dev-ca"
            vb.memory = MASTER_MEMORY
            vb.cpus = 2
            vb.customize ["modifyvm", :id, "--groups", "/minikube-ca"]
        end
        master.vm.provision "ansible" do |ansible|
            ansible.playbook = "minikube-setup/deploy.yml"
        end
    end
end