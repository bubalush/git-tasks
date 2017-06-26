# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |jenkins|

 jenkins.vm.box = "sbeliakou/centos-7.3-x86_64-minimal"
 jenkins.vm.hostname = "jenkins-a-d"

 jenkins.vm.network "private_network", ip: "192.168.123.45"
 jenkins.vm.network "public_network", bridge: "enp4s0"

 jenkins.vm.provider "virtualbox" do |vb|
  vb.memory = "4096"
  vb.name = "jenkins"
 end

 jenkins.vm.post_up_message = "jenkins vm is loaded"
 jenkins.vm.provision "file", source: "./jenkins.service", destination: "jenkins.service"
 jenkins.vm.provision "file", source: "./jenkins.war", destination: "jenkins.war"
jenkins.vm.synced_folder "master/", "/opt/jenkins/master", mount_options: ['dmode=777', 'fmode=777']
 
 jenkins.vm.provision "shell", path: "script_daniil.sh" 
 jenkins.vm.provision "shell", path: "script_aleksei.sh"
end
