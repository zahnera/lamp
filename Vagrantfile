Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.network "forwarded_port", guest:80, host:8080, auto_correct: true
  config.vm.synced_folder ".", "/var/www/html"  
config.vm.provider "virtualbox" do |vb|
  vb.memory = "1024"  
end
config.vm.provision "shell", inline: <<-SHELL
  sudo apt-get update
  sudo apt-get install apache2 libapache2-mod-php7.0 php7.0 php7.0-mysql mysql-server  
SHELL
end