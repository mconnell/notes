# Setup rails stack

apache2
    sudo aptitude install apache2 apache2.2-common apache2-mpm-prefork apache2-utils libexpat1 ssl-cert

ruby + rubygems
    sudo aptitude install ruby-dev ruby ri rdoc irb libreadline-ruby libruby libopenssl-ruby

    cd ~/sources
    wget http://rubyforge.org/frs/download.php/60718/rubygems-1.3.5.tgz
    tar xzvf rubygems-1.3.5.tgz
    cd rubygems-1.3.5.tgz
    sudo ruby setup.rb
    sudo ln -s /usr/bin/gem1.8 /usr/bin/gem

mysql
    sudo aptitude install mysql-server mysql-client libmysqlclient15-dev libmysql-ruby -y
    mysqladmin -u root password YOURMYSQLPASSWORD

postfix
    sudo aptitude install postfix -y

passenger
    sudo gem install passenger
    sudo passenger-install-apache2-module
    sudo apt-get install apache2-prefork-dev libapr1-dev libaprutil1-dev

  add the following to sudo nano /etc/apache2/apache2.conf:
    LoadModule passenger_module /usr/lib/ruby/gems/1.8/gems/passenger-2.2.7/ext/apache2/mod_passenger.so
    PassengerRoot /usr/lib/ruby/gems/1.8/gems/passenger-2.2.7
    PassengerRuby /usr/bin/ruby1.8

Restart Apache
    sudo /etc/init.d/apache2 restart
