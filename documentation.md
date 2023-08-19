# **Web Stack Implementation (LEMP Stack)**

## **What is a LEMP Stack**

A LEMP stack is a powerful combination of software components that collectively form a robust platform for developing and hosting dynamic websites and web applications. The term "LEMP" is an acronym representing the four essential components constituting the stack: Linux, Nginx (pronounced "Engine X"), MySQL, and PHP.

## **Overview of each component of the LEMP Stack**

#### *Linux*
At the foundation of the LEMP stack lies Linux, the operating system that provides the necessary infrastructure for running the other components while efficiently managing hardware resources.

#### *Nginx*
Nginx, an open-source web server software, plays a crucial role in the LEMP stack. It listens to incoming HTTP requests from clients, processes these requests, and delivers web content—such as HTML, CSS, JavaScript—from the server to the clients' web browsers. Nginx excels in its ability to handle high levels of concurrent connections and efficiently serve static content.

#### *MySQL*
MySQL, an open-source relational database management system (RDBMS), is pivotal in the LEMP stack. It facilitates the management and storage of structured data, serving as the repository for data used by web applications. MySQL enables the creation of dynamic websites by enabling interactions with databases, thus supporting data-driven web applications.

#### *PHP*
PHP, a versatile scripting language, is a cornerstone in the LEMP stack. This language is predominantly used for developing dynamic web content and applications. Within the context of the LEMP stack, PHP scripts are embedded within HTML and executed on the server side. These scripts generate dynamic content, which is subsequently transmitted to clients' browsers as HTML. This functionality empowers the creation of interactive and data-driven web applications.

# **The steps in our implementation process include**
### a. Setting up and Connecting to an Ubuntu Virtual Machine

### b. Installing Nginx

### c. Installing MySQL

### d. Installing PHP

### e. Configuring Nginx to use PHP Processor

### f. Testing PHP with Nginx

### g. Retrieving data from MySQL database with PHP

By following these steps, you'll successfully implement a LEMP stack, creating a robust environment to develop and host dynamic web applications.

---

---

## A. **Setting up and Connecting to an Ubuntu Virtual Machine**

---

---

Step 1: Log in to aws and create an ubuntu ec2 instance. 

![Creating an ubuntu ec2 instance](./Images/01.png)

Instance Created!

![Instance Created](./Images/02.png)

---

---

Step 2: Connect to Ubuntu Instance using Instance Connect.

![Connecting to our Ubuntu Instance](./Images/03.png)

Connection Successful!

![Connection Successful](./Images/04.png)

---

---

## B. **Install Nginx**

---

---

Step 3: Update the package repository by running `sudo apt update`

![sudo apt update](./Images/05.png)

---

---

Step 4: Install Nginx by running `sudo apt install nginx`

![sudo apt install nginx](./Images/06.png)

---

---

Step 5: Verify Nginx is running by running `sudo systemctl status nginx`.
If you see a green colored "active(running)", Nginx successfully installed and started on port 80!.

![sudo systemctl status nginx](./Images/07.png)

---

---

Step 6: Open a web browser of your choice (Chrome recommended), navigate to `http://Public-IP-Address-of-ec2:80`

If you see the page below then your web server is correctly installed and accessible through the firewall.

![Nginx home page](./Images/09.png)

---

---

## C. **Install MYSQL**

---

---

Step 7: Use apt to install mysql-server by running `sudo apt install mysql-server`

![sudo apt install mysql-server](./Images/10.png)

---

---


Step 8: Log in to mysql console by running `sudo mysql`

![sudo mysql](./Images/11.png)

---

---

Step 9: Set password for mysql root user by running `ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'PassWord.1';` and exit mysql shell by running `exit`

![mysql code](./Images/12.png)

---

---

Step 10: Improve security by running `sudo mysql_secure_installation`. Answer 'Y' when prompted for each question.

![sudo mysql_secure_installation](./Images/13.png)

---

---

Step 11: Exit mysql shell by running `exit`

![exit](./Images/14.png)

---

---

## D. **Install PHP**

---

---

Step 12: Install PHP and required modules by running `sudo apt install php-fpm php-mysql`. Answer 'Y' when prompted for a question.

![sudo apt install php-fpm php-mysql](./Images/15.png)

---

---

## E. **Configuring Nginx to use PHP Processor**

---

---

Step 13: Create a root web directory for my website by running `sudo mkdir /var/www/projectLEMP`

![sudo mysql](./Images/16.png)

---

---

Step 14: Assign ownership of the directory to current user by running `sudo chown -R $USER:$USER /var/www/projectLEMP`

![Root folder ownership](./Images/17.png)

---

---

Step 15: Open a new Configuration file in the sites available directory by running `sudo nano /etc/nginx/sites-available/projectLEMP` and paste the code below in the file.

```nginx
# /etc/nginx/sites-available/projectLEMP

server {
    listen 80;
    server_name projectLEMP www.projectLEMP;
    root /var/www/projectLEMP;

    index index.html index.htm index.php;

    location / {
        try_files $uri $uri/ =404;
    }

    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php8.1-fpm.sock;
    }

    location ~ /\.ht {
        deny all;
    }
}
```
Save and exit the nano editor with Ctrl + X, then press Y followed by Enter to save your changes. 

---

---

## F. **Testing PHP with Nginx**

---

---

Step 14: To edit the dir.conf file and change the order in which the index.php file is listed, run `sudo nano /etc/apache2/mods-enabled/dir.conf` 

![sudo systemctl status apache2](./Images/17.png)

---

---

## G. **Retrieving data from MySQL database with PHP**

---

---

Step 15: Replace the code you find in dir.conf with this:



---

---

Step 17: Reload apache so that the changes can take effect by running `sudo systemctl reload apache2`

![sudo systemctl status apache2](./Images/18.png)

---

---

Step 18: Create and open a new file inside root your folder by running `sudo nano /var/www/projectlamp/index.php`

![sudo systemctl status apache2](./Images/19.png)

---

---

Step 19: Paste the following php code in the blank file

```php
<?php
phpinfo();
?> 
```
![sudo systemctl status apache2](./Images/20.png)
---

---

Step 20: Open it in browser using `http://localhost/index.php` or `http://yourserveripaddress/test.php` depending on what you have. Should see the image below:
![sudo systemctl status apache2](./Images/21.png)

---

---

Step 22: For security reasons remove the index.php file by running `sudo rm /var/www/projectlamp/index.php`

---

---

# Congratulations! You have successfully installed Apache, MySql and php on your server.

---

---




