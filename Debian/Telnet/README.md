# Telnet Server.
Telnet is a protocol that allows a user to remotely access and manage a device, such as a computer or network router, over a network using a command-line interface Telnet is a clear-text protocol, which means that all data, including passwords, are sent in plain text over the network.  

## Telnet Client tool.

-   **Client Tools Package.**
   
    ```
    # yum install telnet
    ```

-   **Telnet connection with the IP address**

    ```
    telnet IP_address
    ```

## Configure Telnet server.

-   **Install Telnet Server Package.**

    ```
    # apt install telnetd
    ```

-   **Port Allow in iptables.**

    ```
    # iptables -A INPUT -p tcp --dport 23 -j ACCEPT
    ```
    ```
    # iptables-save
    ```
    ```
    # systemctl restart iptables
    ```

-   **Start telnet Service.**

     ```
    # systemctl start inetd
    ```
     ```
    # systemctl enable inetd
    ```
