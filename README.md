# Linux-configuration
IP

   52.89.19.8
   
SSH port

   2200
   
To login as grader

  ssh grader@52.89.19.8 -p2200 -i ~/.ssh/id_rsa
   
  grader user password :- "Udacity123"
   
Complete URL for the web application

   http://ec2-52-89-19-8.us-west-2.compute.amazonaws.com/

Summary of Software Installed

	Full package update/upgrade
	Apache2
	git
	libapache2-mod-wsgi
	postgresql
	python
	pip
	flask
	sqlalchemy
	oauth2client
	http2lib
	requests
	psycopg2
	sqlite

contents of id_rsa.rsa

-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAtoX5lIPdVQym5Kfb9sXow7r9prwT1Q/UdgeDJgAQ9bshBWF4
wQH5Ic5/5k0/1hSI5duNYLWDpZHKk9LRQahTvPY8BC8wjUnB4Cs8eRnjYiFiIb6m
FC4psSo2Yk7RG9P9v+ojgsP3LU9Vvp1BLxiXWF8+VIoN1WO7RSCd2R068yLvMGv1
L34eGhP7VYMvIJ/ydMn1VI3qqEkBJJ/BAvmuPSzW0BqHw9J2NtJi4L0ipyyS+iZd
OkOcNqlT7xcRlZsA1MPYGjRdxf2lwUYoAmc7QtqYunnu9WYbAY+4wwHz6bDvTg4g
qTveboolRORrg92N/GE2WLshGNZruuGdbrE2IwIDAQABAoIBAQCqMDoLVPknuGhV
hH8Bln/3IYAp2+zSGbSNaWvMHvuxZQ7hKYWi0egusZFoeFcxkmwjh5hHuHhMBajS
NRyREBckdqR3cljfJQr1rtrwQEdY1K/frxjEcFbHrwiOmdc5D23naLY70+XCBdt5
pL+G3nMgH47K3P8RHbEcP9FvBGZXFYPPO64et55UB7bE73J8QUqo00RebSdOShQz
n8xxcZy1CWcOVwJBuTFOG0pWo6EQ9LdYE30NEpgh+DYwH0kSkmKX0irG8XB6c/Sc
HDeqyyjTgMTI5uSIakVapodL+hUdkytNgz60VD3G3iOPnQ8e5dO+B5gUjoPItbyk
1WDD/schAoGBAOdUbs8aX6JduN7HJBM+9VJnB78fJh5ikbtebmUc+Pgvya4M7lvh
7gC7OHqWcIy1LHEtL4qwKucqQef9Qf0sf1JZeZ7HsAqxVe+286/5A3eMCxIb9w0Y
kRcUF8hz3LCriSIn9PtAnKOjnVLbNRXihhdANqSSZcoEE/kORaR+YmPtAoGBAMn9
EdriAJWGztvR/o5mzbPeYL8szXk1ihWsgQXC2rJfEecxRot2Za2J5II2xM2giUWX
OoiasAleT9OroVQUiWcnVUXV16CIcheIlZUdVfD/abl8slDh0GIIQ4feIQ1RyzKC
p4gCipwFk2DkYO7KmA1EBRMfgSAWT8XLyTXP2eBPAoGBAJEedZk0qVP5SZVwBiCQ
uWNlQQXTq50aJuQNHGIQJ9vCVtn6QLmhZSZOTOMSZy7OJUAmoZF2bKOx7cB0LyZ8
+K6XdOV3zecXUprcAcmeBF/FmdhVdMlhZPu+XiEhFgw6v/+OY3APG3TImlQ1Mfs1
rPr/DIh3UqXFoyX1nxjPNDgNAoGAHBfJkvLZ9/H+9U3YpL+hnoGwXQaDMXeD1A3h
CAcY2bQlTk1pLV5zN9a05HNvndXVIcutxXAWScdHPP5i+sm8bo9m6cabLeWsUJ+b
hljFKjar4rN4LY2qqOfTVKNNX4ffxg+r81u/IYIZBGHfJXch/L5YIlfAYtEXmUAF
pSlaeTsCgYAZpuoaVEWhv1Cvx76Wr8SFPNAKg1Ub4+s1MoQ5xi+NonwGln2z3hY4
zTkhQuen/IhgCZoG4IVKxH3acOjhrf0NEqMl654sCksI/0Pt5aBZR7ZN1D+PDrwh
//QlpITirvwPiRAqvRiqdlC7OIQ3XFrLvu82ClWbfMJvukvpDcScvA==
-----END RSA PRIVATE KEY-----


    
1. Lauch virtual machine with your Udacity account loggin in.

   Download Private Key Move the private key file into the folder ~/.ssh (where ~ is your environment's home directory). So if you downloaded the file to the Downloads folder, just execute the following command in your terminal.

    mv ~/Downloads/udacity_key.rsa ~/.ssh/

    Open your terminal and type in
    
    chmod 600 ~/.ssh/udacity_key.rsa

    In your terminal, type in
    
    ssh -i ~/.ssh/udacity_key.rsa root@52.89.19.8

2. To Create a new user name grader

   adduser grader
   
   Connect to the user
   
   su - grader

3. To give the grader the permission sudo

    adduser grader sudo

4. In the local machine to create key pair(seperate terminal)

    ssh-keygen

   To copy the key contents to the remote server

    cat .ssh/id_rsa.pub

5. Paste the contents in the remote server key file where the user grader is connected

    touch .ssh/authorized_keys
    
    nano .ssh/authorized_keys

   To Change the autorized_key previlages

    chmod 700 .ssh
    
    chmod 644 .ssh/authorized_keys
   
   To login as grader
   
    ssh grader@52.89.19.8 -p2200 -i ~/.ssh/id_rsa
    
6. To Update all currently installed packages

    sudo apt-get update
    
    sudo apt-get upgrade

7. To change the SSH port from 22 to 2200   

    sudo nano -c /etc/ssh/sshd_config then change port from 22 to 2200
    
    service ssh restart

6. To configure the uncomplicated Firewall(UFW) to only allow incoming connection forSSH (port 2200), HTTP (port 80), and NTP (port 123)

   sudo ufw allow 2200/tcp
   
   sudo ufw allow 80/tcp
   
   sudo ufw allow 123/tcp

7. To Configure the local timezone to UTC

   sudo dpkg-reconfigure tzdata

8. To Install and configure Apache to serve a Python mod_wsgi application

   sudo apt-get install apache2
   
   sudo apt-get install python-setuptools libapache2-mod-wsgi
   

9. To Install and configure PostgreSQL

   sudo apt-get install postgresql postgresql-contrib
   
   sudo apt-get install libpq-dev

10 To Install the required packages for the Item Catalog web application

   sudo pip install flask
   
   sudo pip install sqlalchemy
   
   sudo pip install requests
   
   sudo pip install httplib2
   
   sudo pip install oauth2client

11.To Create a new user named catalog that has limited permissions 

   sudo su - postgres
   psql
   postgres=# CREATE USER catalog WITH PASSWORD 'Pass123';
   # CREATE DATABASE catalog WITH OWNER catalog;
   Connect to the database catalog # \c catalog
   GRANT SELECT, UPDATE, INSERT ON catalog TO catalog;
   \q and exit

12.To Install git, clone and setup Catalog App projec

   sudo apt-get install git
   
   sudo cd/var/www
   
   sudo get clone https://github.com/mahavasu/ItemCatalog

13. To Deploy the Item catalog app

    Create a virtual host config file
    sudo nano /etc/apache2/sites-available/ItemCatalog.conf
    Paste the following contents
    <VirtualHost *:80>
    
      ServerName 52.89.29.8
      
      ServerName admin@52.89.19.8
      
      ServerAlias ec2-52-89-19-8.us-west-2.compute.amazonaws.com

      WSGIScriptAlias / /var/www/ItemCatalog/Item-Catalog.wsgi\
      
      <Directory /var/www/ItemCatalog/ItemCatalog/>
      
          Order allow,deny
          
          Allow from all
          
      </Directory>
      
      Alias /static /var/www/ItemCatalog/ItemCatalog/static
      
      <Directory /var/www/ItemCatalog/ItemCatalog/static/>
      
          Order allow,deny
          
          Allow from all
          
      </Directory>
      
      ErrorLog ${APACHE_LOG_DIR}/error.log
      
      LogLevel warn
      
      CustomLog ${APACHE_LOG_DIR}/access.log combined
      
    </VirtualHost>
    
    Enable the virtual host
    
    sudo a2ensite ItemCatalog
    
   
    Create wsgi file 
    
    cd /var/www/ItemCatalog
    
    sudo nano Item-Catalog.wsgi
    
    Paste the following
    
    #!/usr/bin/python
    
    import sys
    
    import logging
    
    logging.basicConfig(stream=sys.stderr)
    
    sys.path.insert(0, "/var/www/ItemCatalog/")

    from ItemCatalog import app as application
    
    application.secret_key = "Thisissecret"


14. Run the application

    Sudo service apache2 restart

15. To get google authorization go to console.developers.google.com and in the credentials 

    add the webpage address in the java script origins



 
    

