# Table of Contents.
---

| No. | Topic                                                                                  |
| --- | ---------------------------------------------------------------------------------------|
| 1   | [**Introduction Web Server**](#web-server)                                             |
| 2   | [**Introduction Apache Web Server**](#apache-web-server)                               |
| 3   | [**Configure Apache Web Server**](#configure-apache-web-server)                        |
| 4   | [**CSS not properly loadind issues**](#css-not-properly-loadind-issues)                |
| 5   | [**Website Binde with IP**](#website-binde-with-ip)                                    |
| 6   | [**Website Binde with Port**](#website-binde-with-port)                                |
| 7   | [**Website Binde with Domain Name**](#website-binde-with-domain-name)                  |
| 8   | [**Website Binde with SSL**](#website-binde-with-ssl)                                  |
| 9   | [**Website Call with Users home-directory**](#website-call-with-users-home-directory)  |
| 10  | [**Wordpress Deploy in Apache**](#wordpress-deploy-in-apache)                          |

# Web Server.

A web server is a computer program that serves content, such as web pages, to users over the internet. When you access a website, your web browser sends a request to the web server hosting the site, and the server responds by sending back the web page and any related content, such as images or videos.

# Apache Web Server.

Apache is known for its flexibility and reliability, and it is used to host a wide range of websites and applications. It can run on various operating systems, including Linux, Unix, and Windows, and it supports a wide range of programming languages and technologies, including PHP, Perl, and Python.

# Configure Apache Web Server.


-   Install Apache web server in Red Hat Linux.

    ``` 
    yum install httpd*
    ```
-   Usefull Files .
    
    ```
	1. /etc/httpd/conf/httpd.conf
	2. /var/www/html/
    ```
-   Owaner and Group change.

    ```
    chown -Rv apache:apache /var/www/html/*
    ```
-   Port Allow in iptables.

    ```
    vim /etc/sysconfig/iptables
    ```
	    
        -A INPUT -p tcp --dport 80 -j ACCEPT
	
    	-A INPUT -p tcp --dport 443 -j ACCEPT
	
	Note:- Save And Exit using with ':wq!'
	
-   Start iptables service.
    ```
    systemctl start iptables
    ```
    *usage :- This Command Start iptables service.*
    ```
    systemctl restart iptables
    ```
    *usage :- This Command restart iptables service.*
    ```	
    systemctl enable iptables
    ```
    *usage :- This Command enable Booton iptables service.*


## CSS not properly loadind issues. 

- Edit This File
    ```
    vim /etc/httpd/conf/httpd.conf
    ```

	Note Search :- search for Addtype text/html .shtml and insert this two line.
	
	````
    AddType text/css .css
	````

# Website Binde with IP.

-   Edit File.
    ```
    vim /etc/httpd/conf/httpd.conf
    ```	
    Note:- Add these lines at the end of the file.
        
        <Virtualhost  Enter_Your_IP>

        Documentroot /path/to/directory

        Directoryindex index.html

        </virtualhost>

-   Start service.
    ```
    systemctl restart httpd.service
    ```

# Website Binde with Port.

-   Edit File.
    ```
    vim /etc/httpd/conf/httpd.conf
    ```
    Note:- Add these lines at the end of the file.

        Listen Enter_Port_Number
        
        <Virtualhost  Enter_Your_IP>

        Documentroot /path/to/directory

        Directoryindex index.html

        </virtualhost>

-   Start service.
    ```
    systemctl restart httpd.service
    ```

# Website Binde with Domain Name.

-   Create a Local [Domain.](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/DNS%20Server%20Configure.md)

-   Edit File.
    ```
    vim /etc/httpd/conf/httpd.conf
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
    systemctl restart httpd.service
    ```

# Website Binde with SSL.

-   Install SSL
    ```
    yum install mod_ssl
    ```	
-   Edit File.
    ```
    vim /etc/httpd/conf/httpd.conf
    ```
    Note:- Add these lines at the end of the file.
            
        <Virtualhost  Enter_Your_Domain_IP>
            
            SSLEngine on
            
            SSLCertificateFile /etc/pki/tls/certs/localhost.crt
            
            SSLCertificateKeyFile /etc/pki/tls/private/localhost.key
                
            Documentroot /path/to/directory

            Directoryindex index.html
                    
        </virtualhost>

-   Start service.
    ```		
    systemctl restart httpd.service
    ```
# Website Call with Users home-directory.

-   **Enable UserDir**

    ```
    vim /etc/httpd/conf.d/userdir.conf
    ```
-   **Binde website**
    ```
    vim /etc/httpd/conf.d/user_name.conf
    ```
    ```
    <Virtualhost  Enter_Binde_IP>
            Documentroot /home/user_name/public_html
            Directoryindex index.html
    </virtualhost>
    ```

-   **Grant execute permission to user home directory.**
    ```
    cd /home/
    ```
    ```
    chmod 711 user_name
    ```

-   **Go To User**

    Make public_html Directory

    ```
    $ mkdir public_html
    ```
    Put your website in public_html folder.

# Wordpress Deploy in Apache.

-   **Add the some yum repository to your system by running the following command.**

    ```
    yum install epel-release.noarch
    ```
    ```
    yum install remi-release-7.9-4.el7.remi.noarch
    ```
    ```
    yum install elrepo-release-7.0-6.el7.elrepo.noarch
    ```

-   **Install PHP.**

    ```
    yum-config-manager --enable remi-php80 
    ```

    ```
    yum install php php-common.x86_64 php-mcrypt.x86_64 php-cli.x86_64 php-opcache.x86_64 php-gd.x86_64 php-curl php-mysqlnd.x86_64 php-xml.x86_64 php-mbstring.x86_64 mysql-devel php-pear php-mbstring php-pecl-http php-pecl-curl php-session
    ```

-  **Install MySQL.**

    [MysQL.](https://github.com/Mr-Secure-Code/Linux_Server/tree/main/Red%20HAT/MySQL)

-   **Configure phpMyAdmin.**

    ```
    wget https://files.phpmyadmin.net/phpMyAdmin/5.2.0/phpMyAdmin-5.2.0-all-languages.zip
    ```
    ***usage*** :- Install phpMyAdmin Package.
    ```
	tar -xvf phpMyAdmin-latest-all-languages.tar.gz
	```
    ***usage*** :- Unzip phpMyAdmin Package.
    ```	
    cp -rv phpMyAdmin-5.2.0-all-languages /var/www/html/phpMyAdmin
    ```

    **Bind phpMyAdmin any type in your web server.**	
    ```
    vim /etc/httpd/conf/httpd.conf
    ```
    ```
	<Virtualhost Enter_phpMyAdmin_Bind_IP>
   	Documentroot /var/www/html/phpMyAdmin/
    	Directoryindex index.php
	</virtualhost>
    ```

    **Change folder Ownership.**
    ```
    chown -Rv apache:apache /var/www/html/phpMyAdmin
    ```

    **Restart Service**
    ```
    systemctl restart httpd
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
    cp -v wordpress/ /var/www/html/
    ```
    **Bind wordpress any type in your web server.**
    ```
    vim /etc/httpd/conf/httpd.conf
    ```
    ```
    <Virtualhost Enter_phpMyAdmin_Bind_IP>
   	Documentroot /var/www/html/wordpress/
    	Directoryindex index.php
    </virtualhost>
    ```

    **Change folder Ownership.**
    ```
    chown -Rv apache:apache /var/www/html/wordpress/
    ```

    **Disable selinux Permission**
    ```
    vim /etc/sysconfig/selinux
    ```
    ```
    Search 

    SELINUX=enforcing

    Replace

    SELINUX=disable
    ```

    **Restart Service**
    ```
    systemctl restart httpd
    ```
