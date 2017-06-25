# Udacity_LinuxServer
Setup Linux Server and Deploy code

Server: http://54.172.51.47/

SSH: 172.26.13.222

Linux Server Directions

Create Ubunto Lightsail AWS Instance

SSH to remote server

Command: sudo apt-get update

Command: sudo apt-get upgrade

Answer: Y

Command: sudo ufw allow ssh

Command: sudo ufw allow 2200/tcp

Command: sudo ufw allow www

Command: sudo ufw allow ntp

Command: sudo ufw enable

Answer: Y

Command: sudo ufw status

Command: sudo vi /etc/ssh/sshd_config

Edit line : # What ports, IPs and protocols we listen for Port 22 by pressing i

Change to Port 2200 then press esc

Command: :wq

Command: sudo /etc/init.d/ssh restart

Download and convert the private key as found here: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html 


Connect with PuTTy as found here: http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html 

Command: sudo ufw deny ssh

Command: sudo ufw enable

Answer: Y

Command: sudo ufw status

Command: sudo useradd grader

Command: sudo ssh-keygen -f grader

Command: sudo vi grader

Copy private key and store in save location.

Command: sudo dpkg-reconfigure tzdata

Select None of the Aobve

Press Enter

Select UTC

Press Enter

Command: sudo apt-get install apache2 python-setuptools libapache2-mod-wsgi

Answer: Y

Command: sudo apt-get install postgresql

Answer: Y

Command: sudo su – postgres

Command: psql

Command: \q

Command: exit

Command: sudo nano /etc/postgresql/9.5/main/pg_hba.conf

Edit file to update host to local and remote ip addresses to reject

Command: sudo service postgresql restart

Command: sudo su – postgres

Command: psql

Command: CREATE ROLE pythonuser WITH LOGIN PASSWORD 'UserPassword';

Command: CREATE DATABASE catalog;

Command: GRANT ALL PRIVILEGES ON DATABASE catalog TO pythonuser;

Command: \q

Command: exit

Command: sudo apt-get install git

Command: mkdir wwwroot

Command: mkdir git

Command: cd git

Command: mkdir ItemCatalog

Command: cd ItemCatalog

Command: git clone https://github.com/codingwithcookie/Udacity_ItemCatalog.git

Command: cd Udacity_ItemCatalog

Command: sudo apt install python-pip

Command: pip install flask-sqlalchemy

Command: python created.py

Command: pip install oauth2client

Command: pip install requests

Command: python application.py


Command: sudo apt-get install libapache2-mod-wsgi python-dev

Command: sudo a2enmod wsgi

Command: cd /var/www

Command: sudo mkdir ItemCatalog

Copied all the files to that folder.

Command: sudo mv application.py __init__.py

Command: sudo nano /etc/apache2/sites-available/ItemCatalog.conf

Command: sudo nano /var/www/ItemCatalog/ItemCatalog/createDb.py

Command: sudo nano /var/www/ItemCatalog/ItemCatalog/seedDb.py

Update database connection: 'postgresql+psycopg2://pythonuser:UserPassword@localhost/catalog?sslmode=disable'

Command: sudo nano /var/www/ItemCatalog/ItemCatalog/repository.py

Update database connection: 'postgresql+psycopg2://pythonuser:UserPassword@localhost/catalog?sslmode=disable'

Command: sudo service postgresql restart

Command: sudo service apache2 restart
