Vagrant.configure("2") do |config|
  config.vm.box = "bento/ubuntu-18.04"
  config.vm.box_version = "201803.24.0"
  config.vm.network "public_network"
  
  # do NOT install vb guest addtions. The install is erroring out.
  config.vbguest.no_install = true
  config.vbguest.auto_update = true
  
  config.vm.synced_folder ".", "/vagrant", type: "virtualbox"  

  config.vm.provider "virtualbox" do |v|
    v.memory = 3000
    v.cpus = 2
    v.gui = true
  end
	
  config.vm.provider "virtualbox" do |v|
    v.customize ["modifyvm", :id, "--vram", "64"]
#	v.customize ["modifyvm", :id, "--accelerate3d", "on"]
  end	
	
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
	apt-get -y install ansible
	sudo sh -c 'echo "KexAlgorithms diffie-hellman-group1-sha1" >> /etc/ssh/sshd_config'
	service sshd restart
	# apt-get -y install ubuntu-gnome-desktop
	# apt-get -y install ubuntu-desktop
	apt-get -y install kubuntu-desktop
	apt-get -y install git
	apt-get -y install virtualbox-guest-dkms
	apt-get -y install xterm
	#apt-get -y install gnome-shell ubuntu-gnome-desktop

        shutdown -r now
  SHELL
  
  
end

