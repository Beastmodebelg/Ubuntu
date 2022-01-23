# Ubuntu


How to install SSH server in Ubuntu
The procedure to install a ssh server in Ubuntu Linux is as follows:

Open the terminal application for Ubuntu desktop.
For remote Ubuntu server you must use BMC or KVM or IPMI tool to get console access
Type sudo apt-get install openssh-server
Enable the ssh service by typing sudo systemctl enable ssh
Start the ssh service by typing sudo systemctl start ssh

1. Controleer of de service SSH gestart is met het **commando systemctl status** ssh ** – dit is hetzelfde
commando als op SUSE en CentOS.
Als SSH niet aanwezig is, dan moet je deze installeren met het pakketbeheerprogramma **apt-get**
2. a. Op Ubuntu draait de zogenaamde UFW (Uncomplicated Firewall) als beheertool van de
firewall. Daarmee kun je op een eenvoudige manier het onderliggende pakketfilterprogramma,
ip-tables, kunt managen.
De firewall staat na de installatie zeer waarschijnlijk uit. Start deze met het commando:
**ufw enable**
b. Standaard wordt al het inkomende verkeer geblokkeerd. Je zal dan een uitzondering moeten
toevoegen wil je bijv. SSH kunnen gebruiken. Voer het volgende commando uit om SSH toe te
voegen aan de firewall:
**ufw allow 22/tcp**
Controleer met het commando **ufw status** of de regel is toegevoegd.

**ONTBREKENDE PHP MODULES VOOR NEXTCLOUD !**
**sudo apt-get install php zip libapache2-mod-php php-gd php-json php-mysql php-curl php-mbstring php-intl php-imagick php-xml php-zip php-mysql php-bcmath php-gmp -y**

A record voor nextcloud aanmaken 
Forward lookup zone nieuwe zone aanmaken
Dan naam als bijv jlhussle.shrek of nextcloud.local (wat je zelf wilt) als het goed is werkt het dan. Maar dan krijg je** untrusted** domain server**
om dat te fixen ga je naar ubuntu server en doe je cd var/www/html/nextcloud dan doe je cd config dan doe je sudo nano config.php bijvoorbeeld. Op het examen krijg je waarschijnlijk geen config.php maar een ander bestandje. in dat bestandje pas je alles aan zoals bijvoorbeeld de 2de 0 verander je in een 1 en daarachter zet je je a record naam bijv jlhussle.shrek. dan zou die het moeten doen en vergeet natuurlijk je ip niet te veranderen als ie fout staat.

sudo apt update
sudo apt upgrade
Now open ports 22 (for SSH), 80 and 443 and enable Ubuntu Firewall (ufw):

sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
Step 2: Installing and testing Apache2
Install Apache using apt:

sudo apt install apache2
Confirm that Apache is now running with the following command:

sudo systemctl status apache2
You should the get an output showing that the apache2.service is running and enabled.

● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 10:32:26 UTC; 1min 6s ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 52943 (apache2)
      Tasks: 7 (limit: 2282)
     Memory: 11.9M
     CGroup: /system.slice/apache2.service
             ├─52943 /usr/sbin/apache2 -k start
             ├─52944 /usr/sbin/apache2 -k start
             ├─52945 /usr/sbin/apache2 -k start
             ├─52946 /usr/sbin/apache2 -k start
             ├─52947 /usr/sbin/apache2 -k start
             ├─52948 /usr/sbin/apache2 -k start
             └─52953 /usr/sbin/apache2 -k start
Once installed, test by accessing your server’s IP in your browser:

http://YOURSERVERIPADDRESS/
You should see a page with an “Apache2 Ubuntu Default” header showing that Apache2 has been installed successfully. If you do not see this, please ensure that the previous commands in this section have completed without error

Step 3: Installing and testing PHP 7.4
PHP 7.4 is the latest available right now so let’s install that along with some regularly used modules:

sudo apt install php7.4 php7.4-mysql php-common php7.4-cli php7.4-json php7.4-common php7.4-opcache libapache2-mod-php7.4
Check the installation and version:

php --version
Restart Apache for the changes to take effect:

sudo systemctl restart apache2
Create a phpinfo.php test page:

echo '<?php phpinfo(); ?>' | sudo tee -a /var/www/html/phpinfo.php > /dev/null
Test everything is working by accessing the following in your browser:

http://YOURSERVERIPADDRESS/phpinfo.php
You should see a PHP Version 7.4.3 page listing all of your PHP options. If you don’t or it tries to download a file, double-check that all of the above steps have completed without error.

Once you’ve confirmed that PHP is working correctly, delete the test file.

sudo rm /var/www/html/phpinfo.php
The information displayed in the PHP info could be used to find an attack vector against your web server so best not to leave it publicly accessible.

Step 4: Installing and securing MariaDB
MariaDB is a fork of MySQL from some of the original MySQL team and is a drop-in replacement. We’ll be using this over MySQL itself in this guide!

Install the required packages:

sudo apt install mariadb-server mariadb-client
Once installed, check it’s running correctly:

sudo systemctl status mariadb
You should see an output similar to the example below.

● mariadb.service - MariaDB 10.3.25 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 10:33:12 UTC; 4s ago
       Docs: man:mysqld(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 53554 (mysqld)
     Status: "Taking your SQL requests now..."
      Tasks: 31 (limit: 2282)
     Memory: 65.9M
     CGroup: /system.slice/mariadb.service
             └─53554 /usr/sbin/mysqld
Secure your newly installed MariaDB service:

sudo mysql_secure_installation


Step 1: Preparing your Ubuntu server
To begin with, you need a cloud server to run the LAMP stack software. If you are new to UpCloud, have a look at our quick started guide for deploying your first cloud server and how to connect to it.

Once you have your cloud server up and running and connect to it using SSH, you can get started!

First of all, ensure everything is up to date on your server:

**sudo apt update
sudo apt upgrade**
Now open ports 22 (for SSH), 80 and 443 and enable Ubuntu Firewall (ufw):

**sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable**
Step 2: Installing and testing Apache2
Install Apache using apt:

**sudo apt install apache2**
Confirm that Apache is now running with the following command:

**sudo systemctl status apache2**
You should the get an output showing that the apache2.service is running and enabled.

● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 10:32:26 UTC; 1min 6s ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 52943 (apache2)
      Tasks: 7 (limit: 2282)
     Memory: 11.9M
     CGroup: /system.slice/apache2.service
             ├─52943 /usr/sbin/apache2 -k start
             ├─52944 /usr/sbin/apache2 -k start
             ├─52945 /usr/sbin/apache2 -k start
             ├─52946 /usr/sbin/apache2 -k start
             ├─52947 /usr/sbin/apache2 -k start
             ├─52948 /usr/sbin/apache2 -k start
             └─52953 /usr/sbin/apache2 -k start
Once installed, test by accessing your server’s IP in your browser:

**http://YOURSERVERIPADDRESS/**
You should see a page with an “Apache2 Ubuntu Default” header showing that Apache2 has been installed successfully. If you do not see this, please ensure that the previous commands in this section have completed without error

Step 3: Installing and testing PHP 7.4
PHP 7.4 is the latest available right now so let’s install that along with some regularly used modules:

sudo apt install php7.4 php7.4-mysql php-common php7.4-cli php7.4-json php7.4-common php7.4-opcache libapache2-mod-php7.4
Check the installation and version:

php --version
Restart Apache for the changes to take effect:

sudo systemctl restart apache2
Create a phpinfo.php test page:

echo '<?php phpinfo(); ?>' | sudo tee -a /var/www/html/phpinfo.php > /dev/null
Test everything is working by accessing the following in your browser:

**//YOURSERVERIPADDRESS/infophp.php**
You should see a PHP Version 7.4.3 page listing all of your PHP options. If you don’t or it tries to download a file, double-check that all of the above steps have completed without error.

Once you’ve confirmed that PHP is working correctly, delete the test file.

sudo rm /var/www/html/phpinfo.php

**welke versie van ubuntu met lsb_release -d of lsb_release -a en php met php -v enz vermelden in testrapport **

virtual Host aanmaken

sudo mkdir -p /var/www/example.com/public_html

sudo chown -R $USER:$USER /var/www/example.com/public_html

sudo chmod -R 755 /var/www/example.com/public_html

nano /var/www/example.com/public_html/index.html

<html>
  <head>
    <title>Welcome to Example.com!</title>
  </head>
  <body>
    <h1>Success! The example.com virtual host is working!</h1>
  </body>
</html>

cp /var/www/example.com/public_html/index.html /var/www/test.com/public_html/index.html

sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf

sudo nano /etc/apache2/sites-available/example.com.conf

<VirtualHost *:80>
    ServerAdmin admin@example.com
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/public_html
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

sudo a2ensite example.com.conf

sudo a2dissite 000-default.conf

sudo systemctl restart apache2

sudo nano /etc/hosts

127.0.0.1   localhost
127.0.1.1   guest-desktop
your_server_IP example.com


NEXTCLOUD INSTALLEREN
How to install the necessary dependencies
The first thing to be done is the installation of the necessary dependencies. We'll break this into two sections. Log in to your server and access a terminal window. Install the first set of dependencies with the command:

sudo apt-get install apache2 mysql-server -y
When that completes, install the second group of dependencies with the command:

sudo apt-get install php zip libapache2-mod-php php-gd php-json php-mysql php-curl php-mbstring php-intl php-imagick php-xml php-zip php-mysql php-bcmath php-gmp -y
How to secure the MySQL database
With the dependencies out of the way, the next thing to be taken care of is securing the database server. Back at the terminal window, issue the command:

sudo mysql_secure_installation
Give MySQL a new admin password and answer the remaining questions with y (for yes).

How to create the database

Now we'll create the Nextcloud database and a database user. Log in to the MySQL console with the command:

sudo mysql -u root -p
Create the new database with the command:

CREATE DATABASE nextcloud;
Create a new user with the command:

CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'PASSWORD';
Where PASSWORD is a unique and strong password.

Give the new user the necessary permissions with the command:

GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost';
Flush the privileges and exit the console with the commands:

FLUSH PRIVILEGES;
exit
How to download and unpack the Nextcloud file
In order to install Nextcloud, we have to first download the necessary zipped file. To do that, issue the command:

wget https://download.nextcloud.com/server/releases/nextcloud-20.0.0.zip

Unpack that file with the command:

unzip nextcloud-20.0.0.zip
Move the newly-created nextcloud file to the Apache document root with the command:

sudo mv nextcloud /var/www/html/
Next, we'll give the Nextcloud folder the necessary ownership with the command:

sudo chown -R www-data:www-data /var/www/html/nextcloud
How to configure the web server
With the Nextcloud directory in place, we now have to make Apache aware of it. For that, we have to create a .conf file with the command:

sudo nano /etc/apache2/sites-available/nextcloud.conf
In that file, paste the following:

Alias /nextcloud "/var/www/html/nextcloud/"
<Directory /var/www/html/nextcloud/>
    Options +FollowSymlinks
    AllowOverride All
      <IfModule mod_dav.c>
        Dav off
      </IfModule>     

     SetEnv HOME /var/www/html/nextcloud
    SetEnv HTTP_HOME /var/www/html/nextcloud
</Directory>
Save and close the file. 

Enable the new site with the command:

sudo a2ensite nextcloud
We'll now enable the necessary Apache modules by issuing the command:

sudo a2enmod rewrite headers env dir mime
Finally, we'll change the PHP memory limit with the command:

sudo sed -i '/^memory_limit =/s/=.*/= 512M/' /etc/php/7.4/apache2/php.ini
Restart Apache with the command:

sudo systemctl restart apache2
How to finish the installation
Your venture into the command line is complete. Now you can open a browser and point it to http://SERVER_IP/nextcloud (where SERVER_IP is the IP address of the hosting server). You'll first be greeted by the web-based installer (Figure A).

Create a new admin user and fill out the details for the database, which will be:

Database user: nextcloud

Database password: The password you created for the nextcloud database user

Database name: nextcloud

Leave localhost as is and leave Install Recommended Apps checked.

After you've entered the information, click Finish Setup. When the installation completes, you'll find yourself logged in with the Admin user and on the new Nextcloud Dashboard (Figure B).
	
	subnetten

/32	255.255.255.255	
/31	255.255.255.254	
/30	255.255.255.252	
/29	255.255.255.248	
/28	255.255.255.240	
/27	255.255.255.224	
/26	255.255.255.192	
/25	255.255.255.128	
/24	255.255.255.0	
/23	255.255.254.0		
/22	255.255.252.0		
/21	255.255.248.0
/20	255.255.240.0		
/19	255.255.224.0	
/18	255.255.192.0	
/17	255.255.128.0	
/16	255.255.0.0	
/15	255.254.0.0		
/14	255.252.0.0		
/13	255.248.0.0	
/12	255.240.0.0		
/11	255.224.0.0		
/10	255.192.0.0	
/9	255.128.0.0		
/8	255.0.0.0	0	
/7	254.0.0.0	
/6	252.0.0.0	
/5	248.0.0.0	
/4	240.0.0.0	
/3	224.0.0.0	
/2	192.0.0.0		
/1	128.0.0.0		
/0	0.0.0.0		

1. pwd command Use the pwd command to find out the path of the current working directory (folder) you’re in. 
2. cd command cd .. (with two dots) to move one directory up
cd to go straight to the home folder
cd- (with a hyphen) to move to your previous directory
3. ls -R will list all the files in the sub-directories as well
ls -a will show the hidden files
ls -al will list the files and directories with detailed information like the permissions, size, owner, etc.
4. cat (short for concatenate) is one of the most frequently used commands in Linux. It is used to list the contents of a file on the standard output (sdout). To run this command, type cat followed by the file’s name and its extension. For instance: cat file.txt.
5.  rmdir command
6.  locate command
find command
Similar to the locate command, using find also searches for files and directories. The difference is, you use the find command to locate files within a given directory.
grep command
Another basic Linux command that is undoubtedly helpful for everyday use is grep. It lets you search through all the text in a given file.
df command
Use df command to get a report on the system’s disk space usage, shown in percentage and KBs. If you want to see the report in megabytes, type df -m
tar command
The tar command is the most used command to archive multiple files into a tarball — a common Linux file format that is similar to zip format, with compression being optional.
chmod command
chmod is another Linux command, used to change the read, write, and execute permissions of files and directories.
chown command
In Linux, all files are owned by a specific user. The chown command enables you to change or transfer the ownership of a file to the specified username. For instance, chown linuxuser2 file.ext will make linuxuser2 as the owner of the file.ext.
 ping command
Use the ping command to check your connectivity status to a server. For example, by simply entering ping google.com, the command will check whether you’re able to connect to Google and also measure the response time. MAAK EEN SCreenshot van dns a record dat het werkt.
wget command
The Linux command line is super useful — you can even download files from the internet with the help of the wget command. To do so, simply type wget followed by the download link.
echo command
This command is used to move some data into a file. For example, if you want to add the text, “Hello, my name is John” into a file called name.txt, you would type echo Hello, my name is John >> name.txt
zip, unzip command
Use the zip command to compress your files into a zip archive, and use the unzip command to extract the zipped files from a zip archive.

M – Must-haves
Het gaat hier om het minimale eisenpakket dat vooraf gesteld wordt en waaraan het eindresultaat moet voldoen. Zonder deze eis, faalt het project en is het product niet meer bruikbaar.
S – Should-haves
Dit zijn aanvullende en zeer gewenste eisen, die wel een hoge prioriteit hebben, maar geen vereiste zijn voor een bruikbaar eindproduct.
C – Could-haves
Als er tijd voor is kunnen deze eisen altijd nog aan bod komen. Zo niet, dan is het geen probleem en heeft het geen nadelig gevolg voor het eindresultaat. De could-haves hebben minder prioriteit dan de should-haves. 
W – Won’t-haves (en would-haves)
Het gaat hier om toekomstwensen die vaak niet mogelijk zijn of heel veel tijd kosten om te realiseren. Indien niet mogelijk, dan is het verstandig om geen energie hierin te stoppen.

Vergeet niet in t functioneel ontwerp die feedback te doen en in die email memo ook te vragen zodat je doorkan met je technisch ontwerp.
6	Planning
Ten eerste ga ik een behoeftanalyse maken. Vervolgens ga ik een functioneel ontwerp maken. Dan maak ik een technisch ontwerp en tot slot maak ik een testrapportage. Als u nog eventuele vragen heeft kunt u mij bereiken.


**MICHAEL's Manier**
# Lintechno

Step 1: Preparing your Ubuntu server
To begin with, you need a cloud server to run the LAMP stack software. If you are new to UpCloud, have a look at our quick started guide for deploying your first cloud server and how to connect to it.

Once you have your cloud server up and running and connect to it using SSH, you can get started!

First of all, ensure everything is up to date on your server:

sudo apt update
sudo apt upgrade
Now open ports 22 (for SSH), 80 and 443 and enable Ubuntu Firewall (ufw):

sudo ufw allow ssh
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
Step 2: Installing and testing Apache2
Install Apache using apt:

sudo apt install apache2
Confirm that Apache is now running with the following command:

sudo systemctl status apache2
You should the get an output showing that the apache2.service is running and enabled.

● apache2.service - The Apache HTTP Server
     Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 10:32:26 UTC; 1min 6s ago
       Docs: https://httpd.apache.org/docs/2.4/
   Main PID: 52943 (apache2)
      Tasks: 7 (limit: 2282)
     Memory: 11.9M
     CGroup: /system.slice/apache2.service
             ├─52943 /usr/sbin/apache2 -k start
             ├─52944 /usr/sbin/apache2 -k start
             ├─52945 /usr/sbin/apache2 -k start
             ├─52946 /usr/sbin/apache2 -k start
             ├─52947 /usr/sbin/apache2 -k start
             ├─52948 /usr/sbin/apache2 -k start
             └─52953 /usr/sbin/apache2 -k start
Once installed, test by accessing your server’s IP in your browser:

**http://YOURSERVERIPADDRESS/**
You should see a page with an “Apache2 Ubuntu Default” header showing that Apache2 has been installed successfully. If you do not see this, please ensure that the previous commands in this section have completed without error

Step 3: Installing and testing PHP 7.4
PHP 7.4 is the latest available right now so let’s install that along with some regularly used modules:

sudo apt install php7.4 php7.4-mysql php-common php7.4-cli php7.4-json php7.4-common php7.4-opcache libapache2-mod-php7.4
Check the installation and version:

php --version
Restart Apache for the changes to take effect:

sudo systemctl restart apache2
Create a phpinfo.php test page:

echo '<?php phpinfo(); ?>'| sudo tee -a /var/www/html/phpinfo.php > /dev/null
Test everything is working by accessing the following in your browser:

**YOURSERVERIPADDRESS/phpinfo.php**
You should see a PHP Version 7.4.3 page listing all of your PHP options. If you don’t or it tries to download a file, double-check that all of the above steps have completed without error.

Once you’ve confirmed that PHP is working correctly, delete the test file.

**sudo rm /var/www/html/phpinfo.php**
The information displayed in the PHP info could be used to find an attack vector against your web server so best not to leave it publicly accessible.

Step 4: Installing and securing MariaDB
MariaDB is a fork of MySQL from some of the original MySQL team and is a drop-in replacement. We’ll be using this over MySQL itself in this guide!

Install the required packages:

sudo apt install mariadb-server mariadb-client
Once installed, check it’s running correctly:

sudo systemctl status mariadb
You should see an output similar to the example below.

● mariadb.service - MariaDB 10.3.25 database server
     Loaded: loaded (/lib/systemd/system/mariadb.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2020-11-03 10:33:12 UTC; 4s ago
       Docs: man:mysqld(8)
             https://mariadb.com/kb/en/library/systemd/
   Main PID: 53554 (mysqld)
     Status: "Taking your SQL requests now..."
      Tasks: 31 (limit: 2282)
     Memory: 65.9M
     CGroup: /system.slice/mariadb.service
             └─53554 /usr/sbin/mysqld
Secure your newly installed MariaDB service:

sudo mysql_secure_installation

nexcloud install

What you'll need
An instance of Ubuntu Server 20.04

A user account with sudo privileges

Note: You can install Nextcloud on distributions other than Ubuntu Server. I prefer Ubuntu because it's one of the most widely used server platforms (it's the most used Linux distribution on Azure) and it's incredibly user-friendly.

How to install the necessary dependencies
The first thing to be done is the installation of the necessary dependencies. We'll break this into two sections. Log in to your server and access a terminal window. Install the first set of dependencies with the command:

sudo apt-get install apache2 mysql-server -y
When that completes, install the second group of dependencies with the command:

sudo apt-get install php zip libapache2-mod-php php-gd php-json php-mysql php-curl php-mbstring php-intl php-imagick php-xml php-zip php-mysql php-bcmath php-gmp -y
How to secure the MySQL database
With the dependencies out of the way, the next thing to be taken care of is securing the database server. Back at the terminal window, issue the command:

sudo mysql_secure_installation
Give MySQL a new admin password and answer the remaining questions with y (for yes).

How to create the database
Now we'll create the Nextcloud database and a database user. Log in to the MySQL console with the command:

sudo mysql -u root -p
Create the new database with the command:

CREATE DATABASE nextcloud;
Create a new user with the command:

CREATE USER 'nextcloud'@'localhost' IDENTIFIED BY 'PASSWORD';
Where PASSWORD is a unique and strong password.

Give the new user the necessary permissions with the command:

GRANT ALL PRIVILEGES ON nextcloud.* TO 'nextcloud'@'localhost';
Flush the privileges and exit the console with the commands:

FLUSH PRIVILEGES;
exit
How to download and unpack the Nextcloud file
In order to install Nextcloud, we have to first download the necessary zipped file. To do that, issue the command:

wget https://download.nextcloud.com/server/releases/nextcloud-20.0.0.zip
Unpack that file with the command:

unzip nextcloud-20.0.0.zip
Move the newly-created nextcloud file to the Apache document root with the command:

sudo mv nextcloud /var/www/html/
Next, we'll give the Nextcloud folder the necessary ownership with the command:

sudo chown -R www-data:www-data /var/www/html/nextcloud
How to configure the web server
With the Nextcloud directory in place, we now have to make Apache aware of it. For that, we have to create a .conf file with the command:

sudo nano /etc/apache2/sites-available/nextcloud.conf
In that file, paste the following:

Alias /nextcloud "/var/www/html/nextcloud/"
<Directory /var/www/html/nextcloud/>
    Options +FollowSymlinks
    AllowOverride All
      <IfModule mod_dav.c>
        Dav off
      </IfModule>     

     SetEnv HOME /var/www/html/nextcloud
    SetEnv HTTP_HOME /var/www/html/nextcloud
</Directory>
Save and close the file. 

Enable the new site with the command:

sudo a2ensite nextcloud
We'll now enable the necessary Apache modules by issuing the command:

sudo a2enmod rewrite headers env dir mime
Finally, we'll change the PHP memory limit with the command:

sudo sed -i '/^memory_limit =/s/=.*/= 512M/' /etc/php/7.4/apache2/php.ini
Restart Apache with the command:

sudo systemctl restart apache2
How to finish the installation
Your venture into the command line is complete. Now you can open a browser and point it to http://SERVER_IP/nextcloud (where SERVER_IP is the IP address of the hosting server). You'll first be greeted by the web-based installer (Figure A).


THIS IS HOW YOU ALLOW THE PREFERED PORTS ON YOUR UBUNTU


port 80 (http)

port 443 (https)

port 53 (dns



Virtualhost 
cd /var 
cd /www
cd /html
cd /nextcloud
cd /config
sudo nano config.php

(2nd number has to be on zero, but first you have to make an AA-Record in your dns server)

How to install slack on ubuntu
sudo snap install slack --classic

Now that you have Slack installed on your Ubuntu desktop, you can start it either from the command line by typing slack or by clicking on the Slack icon (Activities → Slack).

cat /etc/apt/sources.list.d/slack.list

### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb https://packagecloud.io/slacktechnologies/slack/debian/ jessie main















Project-Opdrachtgever-Auteur-Datum-Versie

 

Inhoud

Opdracht
Aanleiding en Knelpunten
Eisen/Wensen
3.1         Must haves

3.2         Should haves

3.3         Could haves

3.4         Won’t haves

Uit te voeren werkzaamheden
 

OPDRACHT
Beschrijf hier de opdracht die geleid heeft tot het opstellen van deze behoefteanalyse.

 

VOORBEELD:

Thomson Hotels is een keten met ongeveer 280 medewerkers verdeeld over 4 locaties, Zwitserland, Frankrijk Engeland en Nederland. De hoofd directie is in Zwitserland, Hotel Weissburg, de automatisering wordt vanuit Nederland centraal opgezet voor de nieuwe situatie. Comp-U-Serve heef de opdracht gegund gekregen om de automatisering te standaardiseren. Comp-U-serve zal de migratie van het informatie systeem gaan uitvoeren.
Na de migratie zal het dagelijks beheer door de afdeling Systeem Services van het Thomson Hotel worden uitgevoerd

 

 

Aanleiding en Knelpunten
Beschrijf hier de reden die aanleiding waren voor het geven van de opdracht voor het opstellen van deze behoefteanalyse en beschrijf hier de problemen die nu bestaan in de huidige manier van werken.

 

VOORBEELD:

John Thomson wil de automatisering standaardiseren. Hij wil een contract met een extern ICT-bedrijf dat gaat samenwerken met de interne dienst automatisering (System Services). Comp-U-Serve is als partij uit de aanbesteding gekomen. Comp-U-Serve zal de migratie van het informatiesysteem gaan uitvoeren. Na de oplevering zal System Services het informatiesysteem zelf gaan beheren. In Zwitserland is men gewend aan Unix. Ze zien echter de beperkingen en willen eventueel wel overstappen op Linux. In Engeland zijn ze nogal eilandgericht en willen graag vasthouden aan Apple, vooral omdat ze dit vijf maanden geleden volledig hebben geïmplementeerd. Dit is echter gebeurd zonder overleg met de centrale directie. In Frankrijk is

vorig jaar het draadloos netwerk aangelegd. Hier zijn nog steeds veel problemen mee. Er is

geen stabiele verbinding en de beveiliging is al twee keer gekraakt. De bedoeling is dat er één informatiesysteem komt, dat vanaf alle vestigingen toegankelijk is. De vestiging in Maastricht moet alle servers kunnen beheren. Daarnaast moeten de lokale systeembeheerders het centrale beheer kunnen assisteren. Voordat dit project in de operationele omgeving wordt geïmplementeerd, zal er eerst een gedegen ontwerp moeten komen. Ter onderbouwing

en bewijs van het ontwerp is het de bedoeling dat er ook van alle uitgewerkte oplossingen een proefopstelling komt (Proof of Concept).

 

 

Eisen/Wensen
Geef hier een overzicht van de eisen en wensen. Gebruik hier de MoSCoW-onderverdeling

Must haves

Eisen (requirements) die in het eindresultaat moeten terugkomen. Zonder deze eisen is het product niet bruikbaar.

 

Should haves

Eisen die zeer gewenst zijn. Zonder deze functies is het product wel bruikbaar.

 

Could haves

Eisen die alleen aan bod zullen komen als er tijd genoeg is.

 

Won’t haves

Eisen die in dit project niet aan bod komen, maar in de toekomst bij een vervolgproject interessant kunnen zijn.

 

VOORBEELD:

Nieuwe infrastructuur, centraal/decentraal te beheren en internet toegang voor de gasten.

 

 

Uit te voeren werkzaamheden
In dien gevraagd wordt om bepaalde werkzaamheden uit te voeren, worden hier vermeld.


Apache activeren (sudo systemctl start apache2)
Mysql activeren (sudo systemctl start mysql)
Php activeren (sudo systemctl start php)



























How to make a new directory in ubuntu tutorial


inux mkdir Command Syntax
The syntax for the mkdir command is as follows:

mkdir [OPTION] [DIRECTORY]
Copy
The command takes one or more directory names as its arguments.

How to Create a New Directory
To create a directory in Linux, pass the directory’s name as the argument to the mkdir command. For example, to create a new directory newdir, you would run the following command:
mkdir newdir
Copy
You can verify that the directory was created by listing the contents using the ls command :

ls -l
Copy
drwxrwxr-x 2 username username 4096 Jan 20 03:39 newdir
Copy
When providing only the directory name, without the full path, it is created in the current working directory.
The current working directory is the directory from which you are running the commands. To change the current working directory, use the cd command.

To create a new directory in another location, you’ll need to provide the parent directory’s absolute or relative file path. For example, to create a new directory in the /tmp directory you would type:

mkdir /tmp/newdir
Copy
If you try to create a directory in a parent directory where the user does not have sufficient permissions, you will receive Permission denied error:

mkdir /root/newdir
Copy
mkdir: cannot create directory '/root/newdir': Permission denied
Copy
The -v (--verbose) option tells mkdir to print a message for each created directory.

How to Create Parent Directories
A parent directory is a directory that is above another directory in the directory tree. To create parent directories, use the -p option.
Let’s say you want to create a directory /home/linuxize/Music/Rock/Gothic:

mkdir /home/linuxize/Music/Rock/Gothic
Copy
If any of the parent directories don’t exist, you will get an error as shown below:

mkdir: cannot create directory '/home/linuxize/Music/Rock/Gothic': No such file or directory
Copy
Instead of creating the missing parent directories one by one, invoke the mkdir command with the -p option:

mkdir -p /home/linuxize/Music/Rock/Gothic
Copy
When the -p option is used, the command creates the directory only if it doesn’t exist.

If you try to create a directory that already exists and the -p option is not provided, mkdir will print File exists error:

mkdir newdir
Copy
mkdir: cannot create directory 'newdir': File exists
Copy
How to Set Permissions when Creating a Directory
To create a directory with specific permissions, invoke the mkdir commanf with the -m (-mode) option. The syntax for assigning permissions is the same as with the chmod command.

In the following example, we’re creating a new directory with 700 permissions, which means that only the user who created the directory will be able to access it:
mkdir -m 700 newdir
Copy
When the -m option is not used, the newly created directories usually have either 775 or 755 permissions, depending on the umask value.

How to Create Multiple Directories
To create multiple directories, specify the directories' names as the command arguments, separated by space:
mkdir dir1 dir2 dir3
Copy
The mkdir command also allows you to create a complex directory tree with one command:
mkdir -p Music/{Jazz/Blues,Folk,Disco,Rock/{Gothic,Punk,Progressive},Classical/Baroque/Early}
Copy
The command above creates the following directory tree :
