[DNS Theory.](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/DNS%20Theory.md)
# Cache Only DNS.

***Configure Cache Server.***

-   ****Check Hostname.****

    ```
    hostname
    ```

-   **Change Hostname And Domain Name.**

    Edit This File.
    ```
    vim /etc/hostname #hostname.domain-name.top_level_domain_name
    ```

-   **Change DNS.**

    ```
    vim /etc/network/interfaces
    ```

        Searhc DNS
        Enter local ip
        
        DNS1=127.0.0.1

-   **Install Cache Tools.**

    ```
    apt install bind9
    ```

-   **Edit Configure File.**

    ```
    vim /etc/bind/named.conf.options
    ```

        Listen-on port 53 { 127.0.0.1; Your-IP;};

        allow-query {localhost; query-resolve-ip; };


-   **Start Cache Service.**

    ```
    systemctl enable bind9.service
    ```

    ```
    systemctl restart bind9.service
    ```

-   **Enable DNS Port in Firewall.**

    ```
    iptables -A INPUT -p tcp --dport 53 -j ACCEPT
    ```
    ```
    iptables -A INPUT -p udp --dport 53 -j ACCEPT
    ```
    ```
    iptables-save > /etc/iptables/rules.v4
    ```
    ```
    systemctl restart iptables
    ```

# Primary DNS/Master DNS
Primary DNS (Domain Name System) is a server that translates human-readable domain names into numerical IP addresses. When you type a website address into your browser, your computer sends a request to the primary DNS server associated with your internet service provider (ISP) to resolve the domain name into an IP address. The primary DNS server then sends a response with the IP address, which your computer uses to establish a connection to the website's server and load the website.

### Configuration 

**1. Edit File**
```
vim /etc/bind/named.conf.default-zones
```

**2. Make Zone**

![Zone](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Debian/DNS/images/Zone.png?raw=true)

```
1. Zone Name.
2. Zone Type.
3. Zone New Filename (File Extation Match with zone name should be)
```

**3. Make A Zone File**

```
cp -v /etc/bind/db.local /etc/bind/zone_file_name
```

**5. Edit zone File**
```
vim /etc/bind/zone_file_name
```
![Zone File](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Debian/DNS/images/ZoneFile.png?raw=true)

```
First Enter your name server.

second name server.

third make a record.
```

**6.Start Service**

```
systemctl restart bind9
```		

**7. Check Mistacks.**
```		
named-checkconf
```

```
named-checkzone zonename /etc/bind/zone_file_name. 
```

# Forwarders DNS Server


-   **Edit File**
    ```
    vim /etc/bind/named.conf.options
    ```	

-   **search // forwarders And Uncommant fowarders**.

	forwarders { frowardersIP; };
	
-   **Check Forwarders query**

    ```
    tcpdump -n -t udp port 53
    ```
