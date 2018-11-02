# phppgadmin
Install PostgreSQL in XAMPP (PHP 7+) on Windows

# Installing postgreSQL

Download the postgreSQL installer from EnterpriseDB. Download the postgreSQL 9.2 as you might face frequent logout issue.
Run the installer and follow the on-screen instruction.
Assuming XAMPP is located in C:\xampp; using the pgSQL installer, install postgreSQL in say C:\xampp\pgsql\10 folder.
You may skip the Stack Builder section.
You will be prompted to set a password for postgres root user.
By now, pgSQL has been installed.

# Getting postgreSQL to talk with PHP

Open php.ini file located in C:\xampp\php.
Uncomment the following lines in php.ini
extension=php_pdo_pgsql.dll
extension=php_pgsql.dll
Restart Apache
Done.

# Integrating phpPgAdmin to XAMPP – postgreSQL Database Administration tool

To download phpPgAdmin, go to the Github repository and clone the repository to C:\xampp\phppgadmin.
Or download the repository as a Zip, and extract the content to C:\xampp\phppgadmin.
In C:\xampp\phppgadmin\conf, rename the config.inc.php-dist file to config.inc.php
Edit the config.inc.php and replace all instances of the following with the values below
$conf['servers'][0]['host'] = 'localhost';
$conf['servers'][0]['pg_dump_path'] = 'C:\xampp\pgsql\10\bin\pg_dump.exe';
$conf['servers'][0]['pg_dumpall_path'] = 'C:\xampp\pgsql\10\bin\pg_dumpall.exe';
$conf['extra_login_security'] = false;

# Virtual Host Setup In Apache

Edit XAMPP’s httpd-xampp.conf and add the below code.

Alias /phppgadmin "C:/xampp/phppgadmin/"
<directory "C:/xampp/phppgadmin">
AllowOverride AuthConfig
Require all granted
</directory>

Restart Apache

You should now be able to use phpPgAdmin when you visit http://localhost/phppgadmin
