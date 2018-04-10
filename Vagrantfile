#name for VM
VM_NAME = 'lampServer'
#name for User
VM_USER = 'angel'
#host dir for sync
HOST_PATH = 'C:/Users/Angel/dev/devops/vagrant/my-lamp'
#guest dir for sync
GUEST_PATH = '/home/' + VM_USER + '/' + VM_NAME

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.synced_folder HOST_PATH, GUEST_PATH  
  config.vm.hostname = VM_NAME
config.vm.provider "virtualbox" do |vb|
  vb.memory = "1024"
  vb.name = VM_NAME 
  #shows virtualbox gui
  vb.gui = true 
end
config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update
  #set mysql root password
  sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password password Sommer2017'
  sudo debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password Sommer2017'
  #Installation of LAMP components
  sudo apt-get install apache2 libapache2-mod-php7.0 php7.0 php7.0-mysql mysql-server -y
  #sudo apt install openssh-server -y #is already installed
  #sudo apt install phpmyadmin -y #has to be manually installed
SHELL
end