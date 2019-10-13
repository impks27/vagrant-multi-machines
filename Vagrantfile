BOX_IMAGE = "centos/7"
NODE_COUNT = 2

Vagrant.configure("2") do |config|
  config.vm.define "k8s-master" do |subconfig|
    subconfig.vm.box = BOX_IMAGE
    subconfig.vm.hostname = "k8s-master"
    subconfig.vm.network :private_network, ip: "192.168.1.10"
  end
  
  (1..NODE_COUNT).each do |i|
    config.vm.define "k8s-worker-node-#{i}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "k8s-worker-node-#{i}"
      subconfig.vm.network :private_network, ip: "192.168.1.#{i + 10}"
    end
  end

  # Install avahi on all machines  
  config.vm.provision "shell", inline: <<-SHELL
    yum install -y curl 
  SHELL
end

##########################################
#Vagrant.configure("2") do |config|
  #config.vm.define "master" do |subconfig|
    #subconfig.vm.box = "bento/ubuntu-16.04"
  #end

  #config.vm.define "node1" do |subconfig|
    #subconfig.vm.box = "bento/ubuntu-16.04"
  #end

  #config.vm.define "node2" do |subconfig|
    #subconfig.vm.box = "bento/ubuntu-16.04"
  #end
#end