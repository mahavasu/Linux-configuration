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

MIIEpAIBAAKCAQEAyT3q0ukTw3I2Afc9qcQ9Of9YzahsKW5PtgeBg1PzwKkEC9kI
/Ai7vEyc0RPcvjQbQLas9K9riZl8wxd/ENS4vRRPZPw4hdPfPsc5HoqDNnTa9060
5IU3H9mbgyaTgm/JFDSc5ZRdV5ySyWdqZsEa460+EYj1THsLJByZYddEuS1olJ9i
GyaCoIQIWhMq7hujGcwiS+dizC6InhlAzH68xvU26YEebAUHw7OCA22GWtABTohb
rzq8oqQGj7QdhTjwAaKdrBltX96+yiK4RciDpe4FHKRMwhwekKimMh3ZvLPcxaL1
/MBSdSazqk/OVJO/s2SupCXqP9XpMAYPSRV0ewIDAQABAoIBAQCMioJZg087GqMf
IlTdH+CGhY62Kd5H3PMsM/e+CL5dmWvq/kqpAUxjB7ooxc9OwkMaIbmONIhMk3Wv
JdSmo3jVC78azo6G3920ERwR+TgDqv5U4pGwWlySEL3rjOBNotXyF4BPURsTGZTl
tSR42Hl38cA8LMLrA69XK+Xuj5E+JHuZFn5SzJ2jjiuln5GgP7vY0j/E9Tpsr2en
mP3P7T5bvBXHV+qziaaWqX3wenErEehtMHJC/26eGkyrKvzVK27RhZCRtt7/O3LW
KvKUkh8olUBN46Jm3SWcEcGW22AoBCGjYXz2DfTJXRf+LOXBljLb0jpXe/9Ll1Ee
Pj8yZFLZAoGBAPFasFmGWE2KU2VXlwYyIUOnsAgg8rdEAaCNFqHimojdHS2lKxcx
bGzUM+LCVU1lEtFl5CyBKpDp/qwEvYwauXsZKiS1yW2ERg8Hi3bTnPCYUGKh34b8
XtnW9WZv6xHpWv6m7a+SBGF52aCvKZogHf1UTq9fGGyiWn3B6J+scoEVAoGBANV0
GoToWmD1qQ866iJrcCDPDZ4rLIReO2+exNoB4uor4x0ZMOTfTNq4R+0aISgwNgQ8
Va4C4QQKFE3D3aN/j49TVYqz2yECPPNLu/uSTi/z4PCHG5n1D6wG5Z5h+KkTtSuZ
5PTB2a/65LfE/tawD6U4EQj0D0r/gFlWl9TyouNPAoGAGE9DHfFLKZw6JCX7XzNj
aFYWg+sVp2HhLBOp6OpTGF/1FWjiezaOLjP9eeSLBP2eNJsnrVfhOrFm5lqf4OG8
Nurk9MeenzpIeDERWgmccBtXVWfqhMUcpKJjG0tAiRBRCv8zR5DUgiDsy6N49D4x
5xc7yawxYJfFt471aEfNTLUCgYBGaAqLRlzxWHaQKH2sJsYQfFtgjZscejyen78M
rcycMyexpGqFQ8aE6n4HDjRbnjNjCEe2owp3m5+A2xdTY7MFspYnrxWbeLKECboS
y/pwRMAwdlA7YyLtOkUpDeXIV1DN9fAYb4yPSHGC0D7Cr8YpWCn+Swp0UXyTe0WP
nwztbwKBgQDIQFq/ytXL6SnbKvtlnd5bS2294yMQSTP/X9X0t5iDI0PcuI4V8w53
vUyZBP65Ek9mWkuaINxeJBcMsuHPmO/ccCGRSy+fbHUx4Qgh8R2m/cQx/LzhcR+a
WOqOSyXldfkJowC9LyxWkEeeDTXsc8gRNTH8ET/zRWZG4wSjo5kxjQ==
End of private key
    
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
   
    ssh grader@52.89.19.8 -p22 -i ~/.ssh/id_rsa
    
6. To Update all currently installed packages

    sudo apt-get update
    
    sudo apt-get upgrade

7. To change the SSH port from 22 to 2200   

    sudo nano -c /etc/ssh/sshd_config then change port from 22 to 2200
    
    service ssh restart
    
    ssh grader@52.89.19.8 -p2200 -i ~/.ssh/id_rsa

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

10. To Install the required packages for the Item Catalog web application

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
   
   sudo git clone https://github.com/mahavasu/ItemCatalog

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



 
    

