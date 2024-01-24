# Table of Contents.
---

| No. | Topic                                                                                  |
| --- | ---------------------------------------------------------------------------------------|
| 1   | [**Introduction Apache Web Server**](#apache-web-server)                               |
| 2   | [**Configure Apache Web Server**](#configure-apache-web-server)                        |
| 3   | [**Website Binde with IP**](#website-binde-with-ip)                                    |
| 4   | [**Website Binde with Port**](#website-binde-with-port)                                |
| 5   | [**Website Binde with Domain Name**](#website-binde-with-domain-name)                  |
| 6   | [**Website Binde with SSL**](#website-binde-with-ssl)                                  |
| 7   | [**Website Call with Users home-directory**](#website-call-with-users-home-directory)  |
| 8   | [**Wordpress Deploy in Apache**](#wordpress-deploy-in-apache)                          |

# Apache Web Server.

Apache is known for its flexibility and reliability, and it is used to host a wide range of websites and applications. It can run on various operating systems, including Linux, Unix, and Windows, and it supports a wide range of programming languages and technologies, including PHP, Perl, and Python.

# Configure Apache Web Server.


-   Install Apache web server in Debiane Linux.

    ``` 
    apt install apache2*
    ```
-   Usefull Files .
    
    This is the man configuration file.
    ```
	1. /etc/apache2/apache2.conf
    ```
    This is the path to the folder on your server where your web content is stored.
    ```
	2. /var/www/html/
    ```
-   Owaner and Group change.

    ```
    chown www-data:www-data /var/www/html/*
    ```

# Website Binde with IP.

-   Edit File.
    ```
    vim /etc/apache2/apache2.conf
    ```	
    Note:- Add these lines at the end of the file.
        
        <Virtualhost  Enter_Your_IP>

        Documentroot /path/to/directory

        Directoryindex index.html

        </virtualhost>

-   Start service.
    ```
    systemctl restart apache2.service.
    ```

# Website Binde with Port.

-   Edit File.
    ```
    vim /etc/apache2/apache2.conf
    ```
    Note:- Add these lines at the end of the file.
        
        <Virtualhost  Enter_Your_IP: Enter_your_port_number>

        Documentroot /path/to/directory

        Directoryindex index.html

        </virtualhost>

-   Start service.
    ```
    systemctl restart apache2.service
    ```

# Website Binde with Domain Name.

-   Create a Local [Domain.](https://github.com/Mr-Secure-Code/Linux_Server/tree/main/Debian/DNS)

-   Edit File.
    ```
    vim /etc/apache2/apache2.conf
    ```	
    Note:- Add these lines at the end of the file.

        <Virtualhost  Enter_Your_Domain_IP>

        Servername zone.name

        Documentroot /path/to/directory

        Directoryindex index.html

        ServerAlias www.zone.name
                    
        </virtualhost>

-   Start service.
    ```
    systemctl restart apache2.service
    ```

# Website Binde with SSL.

-   Enable ssl module

    ```
    a2enmod ssl
    ```
-   Edit File.
    ```
    vim /etc/apache2/apache2.conf
    ```
    Note:- Add these lines at the end of the file.
            
        <Virtualhost  Enter_Your_Domain_IP>
            
            SSLEngine on
            
            SSLCertificateFile	/etc/ssl/certs/ssl-cert-snakeoil.pem
		
            SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
            
            Documentroot /path/to/directory

            Directoryindex index.html
                    
        </virtualhost>

-   Start service.
    ```		
    systemctl restart apache2.service
    ```
# Website Call with Users home-directory.

-   **Enable the userdir module**

    ```
    a2enmod userdir
    ```
-   **Binde website**
    ```
    vim /etc/apache2/apache2.conf
    ```
    ```
    <Virtualhost  Enter_Binde_IP>
            Documentroot /home/user_name/public_html
            Directoryindex index.html
    </virtualhost>
    ```

-   **Grant execute permission to user.**

    ```
    chmod 711 /home/user_name
    ```

-   **Go To User**

    Make public_html Directory

    ```
    $ mkdir public_html
    ```
    Put your website in public_html folder.
-   Start service.
    ```		
    systemctl restart apache2.service
    ```

# Wordpress Deploy in Apache.

-   **PHP Configure.**

    ```
    apt install php7.4 php7.4-common php7.4-mbstring php7.4-xmlrpc php7.4-soap php7.4-gd php7.4-xml php7.4-intl php7.4-mysql php7.4-cli php7.4-ldap php7.4-zip php7.4-curl 
    ```
    ```
    vim /etc/php/7.4/cli/php.ini
    ```
    ```
    memory_limit = 512M
    max_execution_time = 500
    max_input_vars = 10000
    upload_max_filesize 2048M
    post_max_size = 2048M
    allow_url_fopen = On
    ```
    ```
    memory_limit: Sets the maximum amount of memory that a PHP script is allowed to consume.
	
    max_execution_time: Sets the maximum amount of time that a PHP script is allowed to run.
	
    max_input_vars: Sets the maximum number of variables that a PHP script is allowed to process from external input.

    upload_max_filesize: Sets the maximum size of a file that can be uploaded through a PHP script.

    post_max_size: Sets the maximum size of the HTTP POST data that a PHP script is allowed to process.

    allow_url_fopen: Controls whether PHP scripts are allowed to access remote files using certain functions.
    ```
-  **[MySQL Configure.](https://downloads.mysql.com/docs/mysql-apt-repo-quick-guide-en.pdf)**

    Install MySQL Repo [list.](https://dev.mysql.com/downloads/repo/apt/)
    ```
    wget https://dev.mysql.com/get/mysql-apt-config_0.8.24-1_all.deb
    ```
    ```
    apt install ./mysql-apt-config_0.8.24-1_all.deb
    ```

    Install MySQL-community-server
    ```
    apt update
    ```
    ```
    apt install mysql-community-server
    ```
    After the installation is complete, start the MySQL server using the following command.

    ```
    systemctl start mysqld
    ```
    ```
    systemctl enable mysqld
    ```
    
-   **Configure phpMyAdmin.**

    ```
    wget https://files.phpmyadmin.net/phpMyAdmin/5.2.0/phpMyAdmin-5.2.0-all-languages.zip
    ```
    ***usage*** :- Install phpMyAdmin Package.
    ```
    unzip phpMyAdmin-5.2.0-all-languages.zip
    ```
    ***usage*** :- Unzip phpMyAdmin Package.
    ```	
    cp -rv phpMyAdmin-5.2.0-all-languages /var/www/html/phpMyAdmin
    ```

    **Bind phpMyAdmin any type in your web server.**	
    ```
     vim /etc/apache2/apache2.conf 
    ```
    ```
	<Virtualhost Enter_phpMyAdmin_Bind_IP>
   		Documentroot /var/www/html/phpMyAdmin/
    	 Directoryindex index.php
	</virtualhost>
    ```

    **Change folder Ownership.**
    ```
    chown -Rv www-data:www-data phpMyAdmin/
    ```

    **Restart Service**
    ```
	systemctl restart apache2.service
    ```

-   **Configure Wordpress.**

    Install
    ```
    wget https://wordpress.org/latest.tar.gz
	```
     ***usage*** :- Install wordpress Package.
    ```
	tar -xvf latest.tar.gz
    ```
    ***usage*** :- Unzip wordpress Package.
    ```	
	cp -rv wordpress/ /var/www/html/
	```
    **Bind wordpress any type in your web server.**
    ```
    vim /etc/apache2/apache2.conf
    ```
    ```
    <Virtualhost Enter_phpMyAdmin_Bind_IP>
   		Documentroot /var/www/html/wordpress/
    	Directoryindex index.php
     </virtualhost>
    ```

    **Change folder Ownership.**
    ```
    chown -Rv www-data:www-data /var/www/html/wordpress/
    ```
    
    **Restart Service**
    ```
	systemctl restart apache2.service
    ```
