# Ensure "export VAGRANT_EXPERIMENTAL="disks"
Vagrant.configure("2") do |config|
       config.vm.provider "virtualbox"
#end
  (6..8).each do |i|
       config.vm.define "node#{i}" do |node|
#       node.vm.box = "bento/ubuntu-18.04"
       node.vm.box = "bento/ubuntu-20.04"
#       config.vm.provider "virtualbox"
#      config.vm.define "ansible"
#      config.vm.provision "ansible", playbook: "ubuntu.yml"
       node.vm.network "private_network", ip: "192.168.58.#{i}", auto_config: true
#      config.vm.hostname = "node#{i}"
       node.vm.provider "virtualbox" do |vb|
          # Do not load the command line GUI
          vb.gui = false
#       file_to_disk = "node#{i}.vdi"
#       unless File.exist?"node#{i}.vdi"
#       vb.customize ['createhd', '--filename', file_to_disk, '--size', 20 * 1024]
#  end
       # Virtual Machine Name
       vb.name = "node#{i}"
       vb.memory = "2512"
       vb.cpus = "2"
       # Network settings
       vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
       vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
#
       vb.customize ["modifyvm", :id, "--uart1", "0x3F8", 4]
#       vb.customize ['storageattach', :id, '--storagectl', 'SCSI', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', "node#{i}.vdi"]
#
       config.vm.provision 'shell', path: './01_setup.sh', run: 'always'
       config.vm.provision 'shell', path: './02_setup.sh', run: 'always'
       config.vm.provision "shell", path: './04_setup_init_control.sh', run: 'always'
       config.vm.provision "shell", path: './compute_add.sh', run: 'always'
#       config.vm.provision "shell", path: './05_post_join_control.sh', run: 'always'
#       config.vm.provision 'shell', path: './03.sonqube.sh', run: 'always'
#       config.vm.provision "shell", inline: "usermod -a -G vboxsf vagrant"
#       config.vm.provision "shell", inline: "ln -sf /media/sf_vagrant /vagrant"
#
#      node.vm.network "public_network"
#       node.vm.provision "shell", inline: "sudo sed -i 's/PasswordAuthentication\ no/PasswordAuthentication\ yes/g' /etc/ssh/sshd_config" 
#       node.vm.provision "shell", inline: "echo 10.0.3.7        node7 |sudo  tee -a /etc/hosts" 
#       node.vm.provision "shell", inline: "echo 10.0.3.8        node8 |sudo  tee -a /etc/hosts" 
#       node.vm.provision "shell", inline: "echo 10.0.3.6        node6 |sudo tee -a /etc/hosts" 
#       node.vm.provision "shell", inline: "sudo systemctl restart ssh"
       node.vm.provision "shell", inline: "echo hello from node #{i}"
#
		end
  	end
	end
end
