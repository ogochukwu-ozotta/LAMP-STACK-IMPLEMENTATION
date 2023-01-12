# LAMP-STACK-IMPLEMENTATION

# PROJECT 1 - LAMP WEB STACK IMPLEMENTATION 

## WEB STACK IMPLEMENTATION (LAMP STACK) IN AWS
A technology stack is a set of frameworks and tools used to develop a software product. 
This set of frameworks and tools are very specifically chosen to work together in creating a well-functioning software. 
They are acronymns for individual technologies used together for a specific technology product. some examples are…
LAMP (Linux, Apache, MySQL, PHP or Python, or Perl)

## Project pre-requisite
Login into your Amazon Web Services (AWS) account as an IAM user.
Be sure to create an IAM user if your login as a root user.
Create all resources as an IAM user not root user.

launch a new EC2 instance of t2.micro family with Ubuntu Server 22.04 LTS (HVM)

Once you login into AWS, you will see the main console as follows
![Screen Shot 2022-10-16 at 1 46 10 AM](https://user-images.githubusercontent.com/88560609/196022317-2d540998-f2bd-4c07-ac68-455e7cd2797b.png)

 Select the desired and closest region to you.
 What to consider before creating/hosting resources in AWS:
* Availability
* Latency
* Compliance/Regulation
* Customer location
* Price

![Screen Shot 2022-10-16 at 1 48 11 AM](https://user-images.githubusercontent.com/88560609/196022425-16f65505-61c3-46c2-b98b-5001f19b6593.png)
 
Click on the AWS services on the top left corner
![Screen Shot 2022-10-16 at 1 48 34 AM](https://user-images.githubusercontent.com/88560609/196022464-344c5b7c-e7f9-4175-9758-1dd6dbb626b4.png)

Select Compute to view all the sub-services under compute, then select EC2
![Screen Shot 2022-10-16 at 1 49 16 AM](https://user-images.githubusercontent.com/88560609/196022544-e22a8a3c-0bdd-404c-b84b-a5572a9a80af.png)

From the EC2 dashboard, select Launch Instance
![Screen Shot 2022-10-16 at 1 58 32 AM](https://user-images.githubusercontent.com/88560609/196023421-ea584096-30c2-4064-a88e-9e55cbd67429.png)

A name tag is a label that you assign to an AWS resource. Tags enable you to categorize your AWS resources in different ways, for example, by purpose, owner, or environment. For example, you could define a set of tags for your EC2 instances that helps you track each instance owner and stack level.
Ubuntu Server 22.04 LTS(HVM) 64 bit

![Screen Shot 2022-10-16 at 2 45 57 AM](https://user-images.githubusercontent.com/88560609/196024604-4f80336d-d99f-4c0a-88db-30dc5786de76.png)

Choose an instance type: t2.micro
Leave the 'Network settings' as default

![Screen Shot 2022-10-16 at 2 48 05 AM](https://user-images.githubusercontent.com/88560609/196024745-fae5f196-9488-4c5b-867b-50b4d1e6bcc0.png)

Create key pair: Devops.pem and download
To create a new key-pair, Select "Create a new key-pair" from the drop down menu, give a name to the key-pair, and download it.
IMPORTANT - save your private key (.pem file) securely and do not share it with anyone! If you lose it, you will not be able to connect to your server ever again!

![Screen Shot 2022-10-16 at 2 47 09 AM](https://user-images.githubusercontent.com/88560609/196024762-b2ee9af1-c708-447d-868d-784a936986e3.png)

Configure the 'Firewall (security groups)':
Open SSH, HTTP and HTTPS from Anywhere
A security group acts as a virtual firewall for your EC2 instances to control incoming and outgoing traffic. Inbound rules control the incoming traffic to your instance, and outbound rules control the outgoing traffic from your instance. When you launch an instance, you can specify one or more security groups.

![Screen Shot 2022-10-16 at 2 50 10 AM](https://user-images.githubusercontent.com/88560609/196024915-53a58c47-f23d-4bce-98f3-f25e53e3ddb1.png)

Leave 'Configure storage' and 'Advanced details' as default
Every time you launch an instance from an AMI, a root storage device is created for that instance. The root storage device contains all the information necessary to boot the instance. You can specify storage volumes in addition to the root device volume when you create an AMI or launch an instance using block device.

![Screen Shot 2022-10-16 at 2 50 56 AM](https://user-images.githubusercontent.com/88560609/196024982-1a09ac3e-a5d1-457e-8269-c760d2702b24.png)

Launch the EC2 instance 
View running instance

![Screen Shot 2022-10-16 at 3 01 54 AM](https://user-images.githubusercontent.com/88560609/196025091-58797271-4140-4fc5-a25a-cb718bb372f0.png)

Next is to connect my instance to an SSH Client
Copy the publicIP address for SSH connect in Mac terminal 

![Screen Shot 2022-10-16 at 3 08 45 AM](https://user-images.githubusercontent.com/88560609/196025376-bb4fca2b-9782-4de1-ad57-12d98743aceb.png)

The process to connect to the virtual server is different between Windows and Mac.
Connecting to EC2 Server
Using the terminal on MAC/Linux
The terminal is already installed by default. You just need to open it up.
Use the same key as downloaded from AWS.
Change directory into the loacation where your PEM file is. Most likely will be in the Downloads folder
For Windows, you can use GitBash to achieve same.

```
chmod 400 <key.pem>
```
```
ssh -i key.pem ubuntu@<public-IP-Address>
```
![Screen Shot 2022-10-16 at 3 14 51 AM](https://user-images.githubusercontent.com/88560609/196025545-f29de753-d152-46ce-b29f-1be19eaa844e.png)


For a web application to work smoothly, it has to include an operating system, a web server, a database, and a programming language. The name LAMP is an acronym of the following programs:
* Linux Operating System
* Apache HTTP Server
* MySQL database management system
* PHP programming language

### In this project, I will implement a web solution based on LAMP stack on a Linux server by implementing the steps below:
## STEP 1 — INSTALLING APACHE AND UPDATING THE FIREWALL

Apache HTTP Server is the most widely used web server software. 
Developed and maintained by Apache Software Foundation, Apache is an open source software available for free. 
It runs on 67% of all webservers in the world. It is fast, reliable, and secure. 
It can be highly customized to meet the needs of many different environments by using extensions and modules. 
Most WordPress hosting providers use Apache as their web server software. However, websites and other applications can run on
other web server software as well such as Nginx, Microsoft’s IIS, etc.

The Apache web server is among the most popular web servers in the world. 
It’s well documented, has an active community of users, and has been in wide use for much of the history of the web, which
makes it a great default choice for hosting a website.

Install Apache using Ubuntu’s package manager ‘apt’:
update a list of packages in package manager

```
sudo apt update
```
run apache2 package installation
```
sudo apt install apache2
```
To verify that apache2 is running as a Service in our OS, use following command
```
sudo systemctl status apache2
```
![Screen Shot 2022-10-16 at 3 24 12 AM](https://user-images.githubusercontent.com/88560609/196025891-aa742c16-6261-446c-8f11-8795d588a976.png)

If it is green and running, then you did everything correctly – you have just launched your first Web Server in the Clouds!

To verify and check that we can access it locally in our ubuntu shell and from the internet, run:
```
curl http://localhost:80
or
curl http://127.0.0.1:80
```
As an output you can see some strangely formatted test, do not worry, we just made sure that our Apache web service responds to ‘curl’ command with some payload.
Open a web browser of your choice and try to access following url
```
http://<Public-ip-address>:80
```
Another way to retrieve your Public IP address, other than to check it in AWS Web console, is to use following command:
```
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```
If you see the following page, then your web server is now correctly installed and accessible through your firewall.
see my output:

![Screen Shot 2022-10-16 at 3 30 58 AM](https://user-images.githubusercontent.com/88560609/196026127-6eaa0711-0e28-412d-9ce0-9b7ea5c24bce.png)

## STEP 2 - Installing MySQL

Now that you have a web server up and running, you need to install a Database Management System (DBMS) to be able to store and manage data for your site in a relational database. MySQL is a popular relational database management system used within PHP environments, so we will use it in our project.
```
sudo apt install mysql-server -y
```
It is recommended that you run a security script that comes pre-installed with MySQL. This script will remove some insecure default settings and lock down access to your database system. 

Start the interactive script by running:
```
sudo mysql_secure_installation
```
This will ask if you want to configure the VALIDATE PASSWORD PLUGIN.

Note: Enabling this feature is something of a judgment call. If enabled, passwords which don’t match the specified criteria will be rejected by MySQL with an error.

It is safe to leave validation disabled, but you should always use strong, unique passwords for database credentials.
Answer Y for yes, or anything else to continue without enabling.

```
VALIDATE PASSWORD PLUGIN can be used to test passwords
and improve security. It checks the strength of password
and allows the users to set only those passwords which are
secure enough. Would you like to setup VALIDATE PASSWORD plugin?

Press y|Y for Yes, any other key for No:
```

If you answer “yes”, you’ll be asked to select a level of password validation. 
Keep in mind that if you enter 2 for the strongest level, you will receive errors when attempting to set any password which does not contain numbers, upper and lowercase letters, and special characters, or which is based on common dictionary words.

```
There are three levels of password validation policy:

LOW    Length >= 8
MEDIUM Length >= 8, numeric, mixed case, and special characters
STRONG Length >= 8, numeric, mixed case, special characters and dictionary              file

Please enter 0 = LOW, 1 = MEDIUM and 2 = STRONG: 1
```

Regardless of whether you chose to set up the VALIDATE PASSWORD PLUGIN, your server will next ask you to select and confirm a password for the MySQL root user. 

This is not to be confused with the system root. The database root user is an administrative user with full privileges over the database system. 

Even though the default authentication method for the MySQL root user dispenses the use of a password, even when one is set, you should define a strong password here as an additional safety measure. We’ll talk about this in a moment.

If you enabled password validation, you’ll be shown the password strength for the root password you just entered and your server will ask if you want to continue with that password. If you are happy with your current password, enter Y for “yes” at the prompt:

```
Estimated strength of the password: 100 
Do you wish to continue with the password provided?(Press y|Y for Yes, any other key for No) : y
```

For the rest of the questions, press Y and hit the ENTER key at each prompt.
This will remove some anonymous users and the test database, disable remote root logins, and load these new rules so that MySQL immediately respects the changes you have made.

When you’re finished, test if you’re able to log in to the MySQL console by typing:
```
sudo mysql
```

![Screen Shot 2022-10-16 at 3 44 58 AM](https://user-images.githubusercontent.com/88560609/196026643-1e1384dc-5297-462c-af63-118816772f23.png)

To exit the MySQL Console, type: exit
```
mysql> exit
```

## STEP 4 — INSTALLING PHP

You have Apache installed to serve your content and MySQL installed to store and manage your data. 
PHP is the component of our setup that will process code to display dynamic content to the end user. 
In addition to the php package, you’ll need php-mysql, a PHP module that allows PHP to communicate with MySQL-based databases. 
You’ll also need libapache2-mod-php to enable Apache to handle PHP files. Core PHP packages will automatically be installed as dependencies.

To install these 3 packages at once, run:

```
sudo apt install php libapache2-mod-php php-mysql -y
```

Once the installation is finished, you can run the following command to confirm your PHP version:
```
php -v
```

![Screen Shot 2022-10-16 at 3 48 51 AM](https://user-images.githubusercontent.com/88560609/196026782-2d0e4c22-98f8-4b4b-8c21-f8dc74db8819.png)

At this point, your LAMP stack is completely installed and fully operational.
* Linux (Ubuntu)
* Apache HTTP Server
* MySQL
* PHP

![Screen Shot 2022-10-16 at 3 57 44 AM](https://user-images.githubusercontent.com/88560609/196027097-60c99343-6833-4f7e-b5c1-db4b82b0baa6.png)

To test your setup with a PHP script, it’s best to set up a proper Apache Virtual Host to hold your website’s files and folders.
Virtual host allows you to have multiple websites located on a single machine and users of the websites will not even notice it.

## STEP 5 — CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE

At this step, you will set up a domain called projectlamp, but you can replace this with any domain of your choice.

Apache on Ubuntu 20.04 has one server block enabled by default that is configured to serve documents from the /var/www/html directory.
We will leave this configuration as is and will add our own directory next to the default one.

Create the directory for projectlamp using ‘mkdir’ command as follows:

```
sudo mkdir /var/www/projectlamp
```

Next, assign ownership of the directory with your current system user:
```
sudo chown -R $USER:$USER /var/www/projectlamp
```

Then, create and open a new configuration file in Apache’s sites-available directory using your preferred command-line editor. 
Here, we’ll be using vi or vim (They are the same by the way):

```
sudo vi /etc/apache2/sites-available/projectlamp.conf
```

This will create a new blank file. Paste in the following bare-bones configuration by hitting on i on the keyboard to enter the insert mode, and paste the text:

```
<VirtualHost *:80>
    ServerName projectlamp
    ServerAlias www.projectlamp 
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/projectlamp
    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>
```

![Screen Shot 2022-10-16 at 4 00 44 AM](https://user-images.githubusercontent.com/88560609/196027195-143bbce8-3f2b-4874-9f67-c8ae2f6bffce.png)

To save and close the file, simply follow the steps below:

1. Hit the esc button on the keyboard
2. Type :wq
3. Hit ENTER to save the file
where w is for write and q is for quit
Or, hit the esc button on the keyboard, hold the shift button and type ZZ to quit and save

You can use the ls command to show the new file in the sites-available directory

```
sudo ls /etc/apache2/sites-available
```

![Screen Shot 2022-10-16 at 3 59 22 AM](https://user-images.githubusercontent.com/88560609/196027143-7de6787a-f0ef-45e8-88d3-42fb010f7309.png)

With this VirtualHost configuration, we’re telling Apache to serve projectlamp using /var/www/projectlampl as its web root directory. 
If you would like to test Apache without a domain name, you can remove or comment out the options ServerName and ServerAlias by adding a # character in the beginning of each option’s lines. Adding the # character there will tell the program to skip processing the instructions on those lines.

You can now use a2ensite command to enable the new virtual host:

```
sudo a2ensite projectlamp
```

You might want to disable the default website that comes installed with Apache. 
This is required if you’re not using a custom domain name, because in this case Apache’s default configuration would overwrite your virtual host. 
To disable Apache’s default website use a2dissite command , type:

```
sudo a2dissite 000-default
```

To make sure your configuration file doesn’t contain syntax errors, run:

```
sudo apache2ctl configtest
```

Finally, reload Apache so these changes take effect:

```
sudo systemctl reload apache2

```

![Screen Shot 2022-10-16 at 4 02 36 AM](https://user-images.githubusercontent.com/88560609/196027249-d3b5dd7c-0b38-4dab-8a63-2a01d4d697aa.png)

Your new website is now active, but the web root /var/www/projectlamp is still empty. 
Create an index.html file in that location so that we can test that the virtual host works as expected:

Type and run :
```
sudo vi /var/www/projectlamp/index.html
```
see my input :

![Screen Shot 2022-10-16 at 4 08 31 AM](https://user-images.githubusercontent.com/88560609/196027474-7461a75f-6779-4e7e-91ba-cbd1b6000202.png)

Now go to your browser and try to open your website URL using IP address:

```
http://<Public-IP-Address>:80
```
or you can also browse using your public dns, the result is the same

```
http://<Public-DNS-Name>:80
```

see my output :

![Screen Shot 2022-10-16 at 4 10 47 AM](https://user-images.githubusercontent.com/88560609/196027538-c4b742f6-d116-4f81-8dfe-d31dcfc10826.png)

You can leave this file in place as a temporary landing page for your application until you set up an index.php file to replace it. Once you do that, remember to remove or rename the index.html file from your document root, as it would take precedence over an index.php file by default.

To check your Public IP from the Ubuntu shell, run :
```
curl -s http://169.254.169.254/latest/meta-data/public-hostname
```
```
curl -s http://169.254.169.254/latest/meta-data/public-ipv4
```

## STEP 6 — ENABLE PHP ON THE WEBSITE

With the default DirectoryIndex settings on Apache, a file named index.html will always take precedence over an index.php file. 
This is useful for setting up maintenance pages in PHP applications, by creating a temporary index.html file containing an informative message to visitors. 
Because this page will take precedence over the index.php page, it will then become the landing page for the application. Once maintenance is over, the index.html is renamed or removed from the document root, bringing back the regular application page.

In case you want to change this behavior, you’ll need to edit the /etc/apache2/mods-enabled/dir.conf file and change the order in which the index.php file is listed within the DirectoryIndex directive:

```
sudo vim /etc/apache2/mods-enabled/dir.conf
```

```
<IfModule mod_dir.c>
        #Change this:
        #DirectoryIndex index.html index.cgi index.pl index.php index.xhtml index.htm
        #To this:
        DirectoryIndex index.php index.html index.cgi index.pl index.xhtml index.htm
</IfModule>
```
Before edit:

![Screen Shot 2022-10-16 at 4 17 30 AM](https://user-images.githubusercontent.com/88560609/196027848-a141e59c-8553-44f6-8000-a9362f22e864.png)

After edit:

![Screen Shot 2022-10-16 at 4 19 14 AM](https://user-images.githubusercontent.com/88560609/196027855-8f23d925-bd13-439f-aabc-839eefd87c82.png)

After saving and closing the file, you will need to reload Apache so the changes take effect:

```
sudo systemctl reload apache2
```

Finally, we will create a PHP script to test that PHP is correctly installed and configured on your server.

Now that you have a custom location to host your website’s files and folders, we’ll create a PHP test script to confirm that Apache is able to handle and process requests for PHP files.

Create a new file named index.php inside your custom web root folder:

```
vim /var/www/projectlamp/index.php
```

This will open a blank file. Add the following text, which is valid PHP code, inside the file:

```
<?php
phpinfo();
```

![Screen Shot 2022-10-16 at 4 21 12 AM](https://user-images.githubusercontent.com/88560609/196027939-c6a2cddf-9d6f-4b53-acf2-403b75535f37.png)

When you are finished, save and close the file, refresh the page and you will see a page similar to this:

![Screen Shot 2022-10-16 at 4 22 20 AM](https://user-images.githubusercontent.com/88560609/196027977-36a88aae-066b-4ff5-b172-7b272f56574d.png)

This page provides information about your server from the perspective of PHP. It is useful for debugging and to ensure that your settings are being applied correctly.

If you can see this page in your browser, then your PHP installation is working as expected.

After checking the relevant information about your PHP server through that page, it’s best to remove the file you created as it contains sensitive information about your PHP environment -and your Ubuntu server. You can use rm to do so:

```
sudo rm /var/www/projectlamp/index.php
```

### THE END 
