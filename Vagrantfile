
Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

#Name des hosts
config.vm.hostname = "ServiceLB1"

config.vm.network "public_network", ip:"10.71.13.8"

  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true

  config.vm.synced_folder ".", "/var/www/html"  

config.vm.provider "virtualbox" do |vb|

  vb.memory = "512"  

end

config.vm.provision "shell", inline: <<-SHELL

        sudo apt-get update

        sudo apt-get -y install apache2 
      
      #Webserver installation
        sudo apt-get -y install php libapache2-mod-php
      
      #Debconf installieren, um Prompt befehle zu beantworten
        sudo apt-get install -y debconf-utils
      
      #Prompt befehle für mysq-server
        sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password password asdf123'
      
        sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password asdf123'
      
      #installation mysql-server
        sudo apt-get -y install mysql-server
      
        debconf-set-selections <<< "phpmyadmin phpmyadmin/dbconfig-install boolean true"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/app-password-confirm password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/mysql/admin-pass password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/mysql/app-pass password asdf123"
        debconf-set-selections <<< "phpmyadmin phpmyadmin/reconfigure-webserver multiselect apache2"
      
      #Installation phpMyAdmin
        sudo apt-get -y install phpmyadmin
      
        #sudo echo "Include /etc/phpmyadmin/apache.conf" >> /etc/apache2/apache2.conf
      
        sudo service apache2 restart

      #Installation FireWall
        sudo apt-get install ufw

        sudo ufw -f enable
      
      #FireWall regeln
      sudo ufw allow 22/tcp

        sudo ufw allow 80/tcp

        sudo ufw allow 8080/tcp

#User erstellen
#adduser test
#echo 'view:pass' | chpasswd

SHELL

end
