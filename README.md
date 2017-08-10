# phpBB-using-LAMP-STACK
////Installing LAMP Stack server and deploying phpBB on Ubuntu 16.04(check for other versions of php and mysql according to version of ubuntu and use sudo if asked for permissions)
1.$ sudo apt-get update
2.$ sudo apt-get install apache2
3.$ sudo apache2ctl configtest
4.$ sudo nano /etc/apache2/apache2.conf
5.Then check your apache instance via ServerName/server_domain_or_IP(If servername changed at .conf file apply   servername)
6.Restart apache to implement your changes:
  $ sudo systemctl restart apache2
7.Adjusting firewall to allow traffic
  $ sudo ufw app list
8.Enabling port 80 and 443 
  $ sudo ufw app info "Apache Full"
9.$ sudo ufw allow in "Apache Full"
10.https://your ip address (To Check for Apache)
11.Install MYSQL-Server
   $ sudo apt-get install mysql-server
12.When the installation is complete, we want to run a simple security script that will remove some dangerous defaults and lock down access to our database system a little bit. Start the interactive script by running:
   $ mysql_secure_installation
13.You'll be asked to select a level of password validation. Choose 0 for ease of access.
14.Choose n, When asked
   Change the password for root ? ((Press y|Y for Yes, any other key for No) : 
15.For the rest of the questions, you should press Y and hit the Enter key at each prompt. This will remove some anonymous users and the test database, disable remote root logins.
16. Now install PHP
   $ sudo apt-get install php libapache2-mod-php php-mcrypt php-mysql
17.$ sudo nano /etc/apache2/mods-enabled/dir.conf
18.Replace the contents of the dir.conf
<IfModule mod_dir.c>
    DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
19.$ sudo systemctl restart apache2
20.$ sudo systemctl status apache2
21.$ apt-cache search php- | less
22.$ sudo nano /var/www/html/info.php
23.Paste into info.php file
<?php
phpinfo();
?>
24.Open browser and check for php using "http://your_server_IP_address/info.php"
--------Your LAMP Server is installed and configured at this point-----------

--------Installing phpBB on LAMP Stack-----------------
25. $ cd /var/www/html
26. $ sudo git clone https://github.com/phpbb/phpbb.git
27. $ cd phpbb/
28. $ sudo apt-get install curlsudo curl -s https://getcomposer.org/installer | php
29. $ sudo mv composer.phar /usr/local/bin/composer
30. $ ls
31. $ cd phpBB/
32. $ cd ../
33. $ ls -a
34. $ wget https://github.com/phpbb/phpbb/raw/master/composer.phar
35. $ cd phpBB
36. $ php ../composer.phar
37. $ composer require s9e/text-formatter 
38. $ sudo apt-get install php7.0-intl
39. $ composer require s9e/text-formatter
40. $ cd phpBB/
41. $ php ../composer.phar install
42. $ sudo apt-get install php-curl
43. $ php ../composer.phar install
44. $ sudo apt-get install php-zip
45. $ sudo service apache2 restart
46. $ sudo apt-get install php-mbstring php7.0-mbstring php-gettext libapache2-mod-php7.0
47. $ sudo systemctl restart apache2
48. $ php ../composer.phar install
49. Open phpbb at http://your ip address goes here/phpbb/phpBB/install/app.php
