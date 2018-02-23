# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "bento/centos-7.3"
  config.vm.network "private_network", ip: "192.168.33.100"
  config.vm.provider "virtualbox" do |vb|
      unless File.exist?('./secondDisk.vdi')
        vb.customize ['createhd', '--filename', './secondDisk.vdi', '--variant', 'Fixed', '--size', 10 * 1024]
      end
      unless File.exist?('./thirdDisk.vdi')
        vb.customize ['createhd', '--filename', './thirdDisk.vdi', '--variant', 'Fixed', '--size', 20 * 1024]
      end
      unless File.exist?('./fourthDisk.vdi')
        vb.customize ['createhd', '--filename', './fourthDisk.vdi', '--variant', 'Fixed', '--size', 30 * 1024]
      end

     vb.memory = "4096"
     vb.cpus = "2"
     vb.customize ['storageattach', :id,  '--storagectl', 'SATA Controller', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', './secondDisk.vdi']
     vb.customize ['storageattach', :id,  '--storagectl', 'SATA Controller', '--port', 2, '--device', 0, '--type', 'hdd', '--medium', './thirdDisk.vdi']
     vb.customize ['storageattach', :id,  '--storagectl', 'SATA Controller', '--port', 3, '--device', 0, '--type', 'hdd', '--medium', './fourthDisk.vdi']

  end
end
