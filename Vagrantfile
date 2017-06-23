# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
  config.vm.define "jenkins" do |jenkins|
    jenkins.vm.box = "jenkins"
    jenkins.vm.hostname = 'jenkins'
    jenkins.vm.box_url = "/home/student/git_jenkins/sbeliakou-vagrant-centos-7.3-x86_64-minimal.box"

    jenkins.vm.network :private_network, ip: "192.168.56.23"

    jenkins.vm.provider "virtualbox" do |vb|
      vb.memory = "4096"
      vb.name = "jenkins"
    end
config.vm.provision "shell", inline: <<-SHELL




#---Jenkins----
mkdir /opt/jenkins
mkdir /opt/jenkins/bin
cp /vagrant/jenkins.war /opt/jenkins/bin/jenkins.war
groupadd jenkins
useradd -g jenkins -c "jenkins user" jenkins
echo jenkins | passwd jenkins --stdin


 SHELL
end
end
end
