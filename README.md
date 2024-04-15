Login signup page for flask application + mysql database
STEP 1
Clone directory

Go inside project directory
Cd project/
Now we will see login page flask application files inside another directory 
Installing MySQL Server
STEP 2
Now we have to install database 
sudo apt-get update
sudo apt-get install mysql-server


Check firewall if port is not open for mysql 3306 then open it firstly
STEP 3
sudo status ufw
sudo ufw enable
sudo ufw allow mysql


Now start the mysql service
STEP 4
sudo systemctl start mysql


Installing MySQL Workbench
MySQL Workbench is designed to have either a remote or local MySQL server connection.

STEP 5
Download and install mysql workbench

cd Downloads

sudo apt install ./mysql-apt-config_0.8.16-1_all.deb

sudo apt update

STEP 6
Now enter a database or create new one of name it loginapp1
After entering in mysql
mysql> SHOW DATABASES;
Use loginapp1
CREATE TABLE IF NOT EXISTS accounts (
	id INT AUTO_INCREMENT PRIMARY KEY,
	username VARCHAR(255) NOT NULL,
	password VARCHAR(255) NOT NULL,
	email VARCHAR(255) NOT NULL
);

INSERT INTO accounts (username, password, email) VALUES ('example_user', 'example_password', 'example@example.com');

STEP 7
Create virtual env
py -3 -m venv venv

STEP 8
And activate the env
source venv/bin/activate


Step 9
Install requirements needs to run flask application
pip install -r requirements.txt


STEP 10
Now exit from database and do some change in flask application configuration files to connect them application to database

Go and open main.py file and edited

# Change this to your secret key (can be anything, it's for extra protection)
app.secret_key = '1a2b3c4d5e6d7g8h9i10'

# Enter your database connection details below
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = '*********' #Replace ******* with  your database password.
app.config['MYSQL_DB'] = 'loginapp1'

Esc :wq

My nginx is already configured for this application so no need to change in nginx configuration files
STEP 11
Now we run our login page setup using database(mysql)

sudo nohup python3 app_test.py &


