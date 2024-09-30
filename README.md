# Task 14: AWS EC2 VM Setup, Web Application Deployment, and MySQL Integration

## Objective
This task involves creating a free Virtual Machine (VM) on AWS using EC2, setting up an Apache web server, deploying an HTML page from a previous task, and integrating PHP and MySQL to create a user registration system.

## Steps
### 1. Launch a Free EC2 Instance on AWS
1. Log in to your AWS Management Console.
2. Navigate to **EC2** under **Compute**.
3. Click on **Launch Instance**.

### 2. Connect to the EC2 Instance via SSH
1. Open your Kali Linux terminal.
2. SSH into your EC2 instance using the following command (replace `<your-key.pem>` and `<public-ip>`):
   ```bash
   ssh -i path/to/your-key.pem ubuntu@your-vm-public-ip
   ```
### 3. Clone GitHub Repository from Task 12
1. After logging into the EC2 instance, clone your GitHub repository containing the HTML page:
   ```bash
   git clone https://github.com/yourusername/your-repo.git
   ```
### 4. Install Apache on the EC2 Instance
1. Update the package list:
   ```bash
   sudo apt update
   ```
2. Install Apache:
   ```bash
   sudo apt install apache2 -y
   ```

### 5. Copy Files to Apache Web Server Root
1. Copy the cloned files to the Apache root folder:
   ```bash
   sudo cp -r your-repo/* /var/www/html/
   ```

### 6. Start the Apache Web Server
1. Start the Apache server:
   ```bash
   sudo systemctl start apache2
   ```

### 7. Access the Web Application
1. In your local web browser, go to the following URL to access the web page:
   ```
   http://your-vm-public-ip
   ```
### 8. Install PHP and MySQL
1. Install PHP and MySQL if not already installed:
   ```bash
   sudo apt install php libapache2-mod-php mysql-server -y
   ```
2. Verify that PHP and MySQL are installed:
   ```bash
   php -v
   mysql --version
   ```
here i have installed mariadb instead of mysql becuase of some fault in the mysql server 
### 9. Start Mariadb Server and Log In
1. Start the MySQL service:
   ```bash
   sudo systemctl start mariadb
   ```
2. Log in to Mariadb:
   ```bash
   sudo mysql -u root -p
   ```

### 10. Create Database, Table, and User in MySQL
1. In the MySQL terminal, create a database, user, and table:
   ```sql
   CREATE DATABASE my_database;
   CREATE USER 'my_user'@'localhost' IDENTIFIED BY 'password';
   GRANT ALL PRIVILEGES ON my_database.* TO 'my_user'@'localhost';
   FLUSH PRIVILEGES;
   ```
2. Create a new table in your database:
   ```sql
   USE my_database;
   CREATE TABLE users (
       id INT AUTO_INCREMENT PRIMARY KEY,
       username VARCHAR(50),
       password VARCHAR(50)
   );
   ```

### 11. Create PHP Files for User Registration
1. Create a PHP file (`register.php`) to register users and store data in the MySQL table:
   ```

### 12. Test User Registration
1. Test the user registration page by accessing the PHP form via your browser:
   ```
   http://your-vm-public-ip/register.php
   ```
2. Fill out the form and submit the data to verify that it is saved in the MySQL database.


## Public IP Address
- Your web application can be accessed at: `http://your-vm-public-ip`
