VAGRANTFILE_API_VERSION = "2"



Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
    config.vm.define "web" do |web|

        web.vm.box = "ubuntu/xenial64"
    
        web.vm.hostname = "WebserverLB1"

        web.vm.network "private_network", ip:"192.168.56.10"
    
        #web.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
    
        web.vm.provider "virtualbox" do |vb|
    
          vb.memory = "1000"  
    
        end     
    
          web.vm.synced_folder ".", "/var/www/html"  
    
        web.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update

        sudo apt-get -y install apache2 
      
        sudo apt-get -y install php libapache2-mod-php
      
        sudo apt-get install -y debconf-utils
      
        sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password password asdf123'
      
        sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password asdf123'
      
        sudo apt-get -y install mysql-server

        debconf-set-selections <<< "phpmyadmin phpmyadmin/dbconfig-install boolean true"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/app-password-confirm password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/mysql/admin-pass password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/mysql/app-pass password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/reconfigure-webserver multiselect apache2"
      
        sudo apt-get -y install phpmyadmin
      
        #sudo echo "Include /etc/phpmyadmin/apache.conf" >> /etc/apache2/apache2.conf
      
        sudo service apache2 restart

        sudo apt-get install ufw

        sudo ufw -f enable

        sudo ufw allow 22

        sudo ufw allow 80/tcp

        sudo ufw allow 8080/tcp


        
        #sudo ufw allow from 192.168.56.11 to any http

      SHELL
      
      end

      config.vm.define "proxy" do |proxy|

        proxy.vm.box = "ubuntu/xenial64"
    
        proxy.vm.hostname = "ProxyLB1"

        proxy.vm.network "private_network", ip:"192.168.56.11"
    
        proxy.vm.network "forwarded_port", guest:80, host:5000, auto_correct: true
    
        proxy.vm.provider "virtualbox" do |vb|
    
          vb.memory = "1000"  
    
        end 
        proxy.vm.synced_folder ".", "/vagrant"       
    
        proxy.vm.provision "shell", inline: <<-SHELL

        sudo ufw enable

        sudo ufw allow http

        sudo ufw allow  22/tcp

        apt-get update -y

        apt-get -y install apache2

        a2enmod proxy

        a2enmod proxy_http

        service apache2 restart 
      
      SHELL
      
      end 
    end         