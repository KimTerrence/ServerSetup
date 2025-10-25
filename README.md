```bash
sudo apt install apache2 -y
sudo service apache2 status
cd /etc/apache2/sites-available
sudo cp 000-default.conf 000-default.conf.bak
sudo mv  000-default.conf elogbook.conf
sudo nano elogbook.conf
inside the file, replace html with elogbook
sudo a2ensite elogbook.conf
sudo service apache2 restart
sudo rm -rf /var/www/html
cd /var/www
sudo mkdir elogbook
cd /elogbook
sudo nano index.html
sudo service apache2 restart
enter ip in browser

sudo apt install mysql-server
sudo mysql_secure_installation
all y
1
sudo MySQL -u root -p
create database logbook_db;
create user 'borrowing_user'@'localhost' identified by '#Zuchini1234';
grant all privileges on logbook_db* to 'borrowing_user'@'localhost';
flush privileges;
exit


sudo apt install php -y
sudo apt install php libapache2-mod-php php-mysql -y
sudo nano index.php
<?php echo phpinfo(); ?>
sudo service apache2 restart
go to browser
s

search on browser phpMyAdmin download
copy link English.zip
wget https://files.phpmyadmin.net/phpMyAdmin/5.2.2/phpMyAdmin-5.2.2-english.zip
sudo apt install unzip -y
unzip phpMyAdmin-5.2.2-english.zip
sudo mv phpMyAdmin-5.2.2-english database
sudo mv database /var/www/elogbook
go to browser: ip/database/index.php
login :borrowing_user pw:#Zuchini1234



sudo ufw allow 80 (u will see rules updated (v6)
sudo ufw enable
y
you will see firewall is active
exit
try ssh and it will be permission denied
go back to ubuntu 
sudo ufw allow 22
sudo ufw enable
then go back to cmd and ssh again


cd /var/www/elogbook
sudo nano .htaccess
write this inside the file:
"RewriteEngine on
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME}\.php -f
RewriteRule ^(.*)$ $1.php

Options -Indexes"
cd /etc/apache2
sudo nano apache2.conf
find <Directory /var/www/>
"<Directory /var/www/>
        Options -Indexes
        AllowOverride All
        Require all granted
</Directory>" # this should be the content of this
cd /var/www
sudo chown -R www-data:www-data elogbook/
sudo chmod -R 755 elogbook/
sudo a2enmod rewrite
sudo service apache2 restart

notes from Zuchini Nunez
```
