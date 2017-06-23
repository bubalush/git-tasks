Vagrant.configure("2") do |config|
  config.vm.define "jenkins" do |jenkins|
	jenkins.vm.box = "sbeliakou-vagrant-centos-7.3-x86_64-minimal.box"
	jenkins.vm.network "private_network", ip: "192.168.56.50"
	jenkins.vm.hostname = "jenkins"
	jenkins.vm.provider :virtualbox do |v|
		v.customize ["modifyvm", :id, "--name", "jenkins"]
	end
	jenkins.vm.provision "shell", inline: <<-SHELL
		yum -y install java-1.8.0-openjdk-devel
		yum -y install nginx
		sed -i '39,44d;46,56d' /etc/nginx/nginx.conf
		cat > /etc/nginx/default.d/redir_serv.conf << EOL
        listen       80;
        server_name  jenkins;

        location / {
                proxy_pass http://localhost:8080;
		proxy_redirect  http://localhost:8080 $scheme://jenkins;
        }

        error_page 404 /404.html;
            location = /40x.html {
        }

        error_page 500 502 503 504 /50x.html;
            location = /50x.html {
        }
EOL
		systemctl enable nginx.service
		systemctl start nginx.service
	SHELL
  end
end
