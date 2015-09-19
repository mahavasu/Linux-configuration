# Linux-configuration
IP
 52.89.75.35
SSh port 
 2200

1. Lauch virtual machine with your Udacity account loggin in.

   Download Private Key Move the private key file into the folder ~/.ssh (where ~ is your environment's home directory). So if you downloaded the file to the Downloads folder, just execute the following command in your terminal.

    mv ~/Downloads/udacity_key.rsa ~/.ssh/
    Open your terminal and type in
    chmod 600 ~/.ssh/udacity_key.rsa
    In your terminal, type in
    ssh -i ~/.ssh/udacity_key.rsa root@52.89.75.35
    
2. To Create a new user name grader

    adduser grader
    
3. To give the grader the permission sudo

    adduser grader sudo
    
4. To Update all currently installed packages

    sudo apt-get update
    sudo apt-get upgrade
    
5. To change the SSH port from 22 to 2200   

  sudo nano -c /etc/ssh/sshd_config
  /etc/init.d/sshd restart
  
6. To configure the uncomplicated Firewall(UFW) to only allow incoming connection forSSH (port 2200), HTTP (port 80), and NTP (port 123)

   sudo ufw allow 2200/tcp
   sudo ufw allow 80/tcp
   sudo ufw allow 123/tcp
   
7. To Configure the local timezone to UTC

   sudo dpkg-reconfigure tzdata
   
8. To Install and configure Apache to serve a Python mod_wsgi application

   sudo apt-get install python-pip apache2 libapache2-mod-wsgi
   sudo a2enmod wsgi 
   
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
   postgres=# CREATE USER catalog WITH PASSWORD 'secure password';
   postgres=# GRANT SELECT, UPDATE, INSERT ON catalog TO catalog;
   postgres=# \q
   exit
   
12.To Install git, clone and setup Catalog App projec
  sudo apt-get install git
  sudo cd/var/www
  sudo get clone https://github.com/mahavasu/Item-Catalog

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
