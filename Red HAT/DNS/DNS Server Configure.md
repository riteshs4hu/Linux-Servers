# Cache Only DNS.

***Configure Cache Server.***

****Check Hostname.****

```
# hostname
```

**Change Hostname And Domain Name.**

Edit This File.
```
# vim /etc/hostname #hostname.domain-name.top_level_domain_name
```

**Change DNS.**

```
# vim /etc/sysconfig/network-scripts/ifcfg-enp0s3
```

    Searhc DNS
    Enter local ip
	
	DNS1=127.0.0.1

**Install Cache Tools.**

```
# yum install bind*
```

**Edit Configure File.**

```
# vim /etc/named.conf
```
    Listen-on port 53 { 127.0.0.1; Your-IP;};

    allow-query {localhost; query-resolve-ip; };

**Start Cache Service.**

```
# systemctl enable named.service
```

```
# systemctl restart named.service
```

**Enable DNS Port in Firewall**

```
# vim /etc/sysconfig/iptables
```
    -A INPUT -p UPD --dport 53 -j ACCEPT
```
# systemctl restart iptables
```

# Primary DNS/Master DNS
Primary DNS (Domain Name System) is a server that translates human-readable domain names into numerical IP addresses. When you type a website address into your browser, your computer sends a request to the primary DNS server associated with your internet service provider (ISP) to resolve the domain name into an IP address. The primary DNS server then sends a response with the IP address, which your computer uses to establish a connection to the website's server and load the website.

## Type of Primary dns/Master dns

-  **Forwarder Zone**

   A Forward DNS lookup is used to convert a domain name to an IP address.
-  **Revers Zone**
    
    A reverse DNS lookup is used to convert an IP address to a domain name.

### Forwarder Zone Configuration 

**1. Edit File**
```
# vim /etc/named.rfc1912.zones
```

**2. Make Zone**

![Zone](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/Zone.png?raw=true)

```
1. Zone Name.
2. Zone Type.
3. Zone New Filename (File Extation Match with zone name should be)
```

**3. Make A Zone File**

```
# cp /var/named/named.localhost /var/named/zone_file_name
```

**4. Change file group**
```
# chgrp named /var/named/zone_file_name
```
**5. Edit zone File**
```
# vim /var/named/zonefilename
```
![Zone File](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/ZoneFile.png?raw=true)

```
First Enter your name server.

second name server.

third make a record.
```

**6.Start Service**

```
# systemctl restart named
```		

**7. Check Mistacks.**
```		
# named-checkconf
```

```
# named-checkzone zonename /var/named/zone_file_name. 
```
### Reverse Zone Configuration.


**1. Make A Reverse Zone**

```
# vim /etc/named.rfc1912.zones
```
![Reverse Zone](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/Revers%20Zone.png?raw=true)

```
1. Enter Network IP Revers Order.

2. Enter Any Name File.
```

**2. Make Zone File**

```
# cp /var/named/named.localhost /var/named/zone_file_name.
```

**3. Edit Zone File**

```
# vim /var/named/zone_file_name
```

![Reverse Zone File](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/Revers%20Zone%20File.png?raw=true)

```
1. Enter Your Name Server.
2. Enter Your Name Server.
3. Your Name Server PTR Record.
4. other Records.
```
**4. Change File Group.**

```
# chgrep named zone_file_name.
```

**5. Start Service**

```
# systemctl restart named
```

# Seconder/Slave DNS

**1. Make A Secondery Zone.**

![Slave Zone](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/Slave%20Zone.png?raw=true)

```
First enter master server name.

Second enter zone type.

third enter zone file name.

fourth Enter master dns IP.

```

**2. Start Service.**

```
# systemctl restart named
```		

**3. Change Primery Dns Settings.**

![Master Changes](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/DNS/Images/Master%20Changes.png?raw=true)

```
First enter your primery name server.

Second enter primery name server.

third enter slave name server.

fourth make A records.
```

**4. Restart Service.**
```
# systemctl restart named
```

# Forwarders DNS Server


**Edit File**
```
# vim /etc/named.conf
```	
**search recursion And insert This Line**.

	
	forwarders { frowardersIP; };
	
**Check Forwarders query**

```
# tcpdump -n -t udp port 53
```
