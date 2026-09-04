#steps to host dynamic website using 'LAMP techstack'

1. Clone the project from GitHub repo 
	> git clone "https://github.com/sangeethaSam17/php-project.git"

2. install apache2, mysql, php
> sudo apt update
> sudo apt install -y apache2 mysql-server php libapache2-mod-php
> sudo apt install -y php-cli php-common php-mysql php-curl php-mbstring php-xml php-zip php-gd

3. check the status of apache2 and mysql
> systemctl start apache2
> systemctl start mysql

4. host the files (index.php) to /var/www/html/
> sudo cp -r "./carrental/* /var/www/html/"


5. Change database login credential
> sudo mysql
#inside mysql
    > select user,host,plugin from mysql.user
    > ALTER USER 'root'@'localhost'
    > IDENTIFIED WITH caching_sha2_password BY '<your_password>';
    > FLUSH PRIVILEGES;


6. copy the database configure from "./SQL FILE/carrental.sql" to carrental database
> mysql -u root -p carrental < "/home/suhas/php-project/SQL File/carrental.sql"
NOTE: change the file path according your system "/home/suhas/php-project/SQL File/carrental.sql"

7. Update db password in config.php file
path: ./php-project/carrental/includes/config.php


9. Restart apache2
> sudo systemctl reload apache2 



9. Open the browser and provide the url to access app
"http://localhost:4444/index.php"
