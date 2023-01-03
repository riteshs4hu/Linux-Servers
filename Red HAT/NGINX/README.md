# Table of Contents.
---

| No. | Topic                                                                     |
| --- | --------------------------------------------------------------------------|
| 1   | [**Introduction NGINX Server**](#nginx-web-server)                        |
| 2   | [**Configure NGINX Web Server**](#configure-nginx-web-server)             |
| 3   | [**Website Binde with IP**](#website-binde-with-ip)                       |
| 4   | [**Website Binde with Port**](#website-binde-with-port)                   |
| 5   | [**Website Binde with Domain Name**](#website-binde-with-domain-name)     |
| 6   | [**Website Binde with SSL**](#website-binde-with-ssl)                     |

# NGINX Web Server.

NGINX is known for its event-based architecture, which allows it to handle a large number of concurrent connections using a small number of worker processes. This makes it well-suited for high-traffic environments, and it is often used to improve the performance of web applications.


# Configure NGINX Web Server.


-   Install NGINX web server in Red Hat Linux.

    ``` 
    # yum install nginx*
    ```
-   Usefull Files .
    
    This is the man configuration file.
    ```
	1. /etc/nginx/nginx.conf
    ```
    This is the path to the folder on your server where your web content is stored.
    ```
	2. /usr/share/nginx/html/
    ```
-   Owaner and Group change.

    ```
    chown -Rv nginx:nginx /usr/share/nginx/html/*
    ```
-   Port Allow in iptables.

    ```
    # vim /etc/sysconfig/iptables
    ```
	    
        -A INPUT -p tcp --dport 80 -j ACCEPT
	
    	-A INPUT -p tcp --dport 443 -j ACCEPT
	
	Note:- Save And Exit using with ':wq!'
	
-   Start iptables service.
    ```
    # systemctl start iptables
    ```
    *usage :- This Command Start iptables service*
    ```
    # systemctl restart iptables
    ```
    *usage :- This Command restart iptables service*
    ```	
    # systemctl enable iptables
    ```
    *usage :- This Command enable Booton iptables service*

# Website Binde with IP.

-   Edit Configure file.
    ```
    # vim /etc/nginx/nginx.conf
    ```	
    Note:- Go To server block.
    ```
    1. listen       Enter Your_IPv4;
    2. listen       Enter_Your_IPv6;
    4. root         /path/to/website;
    ```
    
    This is the path to the folder on your server where your web content is stored.

    ```
    /usr/share/nginx/html/your_web_site Or your_web_contain_folder
    ```
-   Start service.
    ```
    # systemctl restart nginx.service
    ```

# Website Binde with Port.

-   Edit Configure file.
    ```
    # vim /etc/nginx/nginx.conf
    ```	
    Note:- Go To server block.
    ```
    1. listen     Enter Your_IPv4 : Enter_port_number;
    2. listen     Enter_Your_IPv6 : Enter_port_number;
    4. root       /path/to/website;
    ```
    
    This is the path to the folder on your server where your web content is stored.

    ```
    /usr/share/nginx/html/your_web_site Or your_web_contain_folder
    ```
-   Start service.
    ```
    # systemctl restart nginx.service
    ```

# Website Binde with Domain Name.

-   Create a Local [Domain.](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/DNS%20Server%20Configure.md)

-   Edit Configure file.
    ```
    # vim /etc/nginx/nginx.conf
    ```	
    Note:- Go To server block.
    ```
    1. listen       Enter Your_IPv4 : Enter_port_number;
    2. listen           Enter_Your_IPv6 : Enter_port_number;
    3. server_name      Enter_your_domain/local_domain;
    4. root            /path/to/website;
    ```
    
    This is the path to the folder on your server where your web content is stored.

    ```
    /usr/share/nginx/html/your_web_site Or your_web_contain_folder
    ```
-   Start service.
    ```
    # systemctl restart nginx.service
    ```
# Website Binde with SSL.

-   Install SSL
    ```
    # yum install mod_ssl
    ```	
-   Edit Configure file.
    ```
    # vim /etc/nginx/nginx.conf
    ```	
    Note:- Go To server block.
    ```
    1. listen           Enter Your_IPv4 : Enter_port_number ssl;
    2. listen           Enter_Your_IPv6 : Enter_port_number;
    3. root            /path/to/website;
    ```
    Add This Two line.
    ```
    ssl_certificate /etc/pki/tls/certs/localhost.crt;
    ssl_certificate_key /etc/pki/tls/private/localhost.key; 
    ```
    
    This is the path to the folder on your server where your web content is stored.

    ```
    /usr/share/nginx/html/your_web_site Or your_web_contain_folder
    ```
-   Start service.
    ```
    # systemctl restart nginx.service
    ```
