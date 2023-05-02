# Telnet Server.
Telnet is a protocol that allows a user to remotely access and manage a device, such as a computer or network router, over a network using a command-line interface Telnet is a clear-text protocol, which means that all data, including passwords, are sent in plain text over the network.  

## Telnet Client tool.

-   **Client Tools Package.**
   
    ```
    yum install telnet
    ```

-   **Telnet connection with the IP address**

    ```
    telnet IP_address
    ```

## Configure Telnet server.

-   **Install Telnet Server Package.**

    ```
    yum install telnet-server xinetd
    ```
-   **Make telnet service file**

    ```
    vim /etc/xinetd.d/telnet
    ```
        service  telnet
        {
        flags           = REUSE
        socket_type     = stream
        wait            = no
        user            = root
        server          = /usr/sbin/in.telnetd
        log_on_failure += USERID
        disable         = no
        }

-   **Port Allow in iptables.**

    ```
    iptables -A INPUT -p tcp --dport 23 -j ACCEPT
    ```
    ```
    iptables-save
    ```
    ```
    systemctl restart iptables.service 
    ```
-   **Start telnet service.**

    ```
    systemctl enable telnet.socket
    ```
    ```
    systemctl restart telnet.socket
    ```
    ```
    systemctl enable xinetd.service
    ```
    ```
    systemctl restart xinetd.service
    ```

-   **Enable root User**

    ```
    vim /etc/securetty
    ```
    **Note:-** Go to end of the file and insert this lines. 
        
        pts/0
        pts/1
        pts/2
        pts/3
        pts/4
        pts/5
        pts/6
        pts/7
        pts/8
        pts/9

    **Retart telnet service.**

    ```
    systemctl restart xinetd.service
    ```
