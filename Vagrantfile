Vagrant.configure("2") do |config|
  config.vm.box = "gbailey/amzn2"
  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end
  config.vm.provision "shell", inline: <<-SHELL
    fixfiles onboot
    sed -i -e 's/^SELINUX=.*/SELINUX=permissive/' /etc/selinux/config
  SHELL
  config.vm.provision :shell do |shell|
      shell.privileged = true
      shell.inline = 'echo rebooting'
      shell.reboot = true
  end
  config.vm.provision "shell", inline: <<-SHELL
    fixfiles onboot
    sed -i -e 's/^SELINUX=.*/SELINUX=enforcing/' /etc/selinux/config
  SHELL
  config.vm.provision :shell do |shell|
      shell.privileged = true
      shell.inline = 'echo rebooting'
      shell.reboot = true
  end
end
