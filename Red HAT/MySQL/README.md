# MySQL Community Server Configuration.

- Add the some yum repository to your system by running the following command.

    ```
    yum install epel-release.noarch
    ```
    ```
    yum install remi-release-7.9-4.el7.remi.noarch
    ```
    ```
    yum install elrepo-release-7.0-6.el7.elrepo.noarch
    ```

-   Add the MySQL port (3306) to the firewall by running the following command.

    ```
    iptables -A INPUT -p tcp --dport 3306 -j ACCEPT
    ```
    ```
    service iptables save
    ```
-   Restart the iptables service to apply the changes.
    ```
    systemctl restart iptables
    ```
-   Update the package manager cache by running the following command.
    ```
    yum update
    ```
-   Install PHP Packages by running the following command.
    ```
    yum install php php-common.x86_64 php-mcrypt.x86_64 php-cli-5.4.16-48.el7.x86_64 php-opcache.x86_64 php-gd.x86_64 php-curl php-mysqlnd.x86_64 php-xml.x86_64 php-mbstring.x86_64
    ```
- Add the MySQL Yum repository to your system by running the following command.

    ```
    yum install https://dev.mysql.com/get/mysql80-community-release-el7-7.noarch.rpm
    ```
-  Install the MySQL Community Server package by running the following command.
    ```
    yum install mysql-community-server
    ```
    ```
    yum install mysql-community-embedded-compat-8.0.31-1.el7.x86_64
    ```

    ```
    yum install mysql-community-devel-8.0.31-1.el7.x86_64
    ```

-   After the installation is complete, start the MySQL server using the following command.

    ```
    systemctl start mysqld
    ```
    ```
    systemctl enable mysqld
    ```
-  Get MySQL temporary password using the following command.
 
    ```
    grep 'temporary password' /var/log/mysqld.log
    ```
-   Change MySQL Password using the following command.
    ```
    mysql_secure_installation
    ```
