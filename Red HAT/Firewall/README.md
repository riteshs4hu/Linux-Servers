# What is Firewall.

A firewall is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. A firewall can be hardware-based, software-based, or a combination of both.

# How firewalls are managed.
The **input**, **forward**, and **output** chains are all used to control and monitor traffic in a firewall, helping to protect the network or device from external threats and ensure that only authorized traffic is allowed to pass through.

## Firewall Configure.

**Install Firewall tools.**
```
yum install iptables
```

**Start iptables service**
```
systemctl restart iptables.service
```
```
systemctl enable iptebles.service
```

**Manage Table.**
```
iptables --help
```     
```
iptables -L
```             
```
iptables -L -n --line-number
```
```
iptables -n -L INPUT               
```
``` 
iptables -n -L OUTPUT
```     
```
iptables -n -L FORWARD
```
**Temporary Configure**

```
iptables -I INPUT 5 -p tcp --dport 21 -j ACCEPT
```     
```
iptables -I INPUT 5  -p tcp --dport 80:90 -j ACCEPT
```     
```
iptables -I INPUT 1 -p tcp --dport telnet -j ACCEPT
```
```
iptables -I INPUT 5 -p udp --dport 53 -j ACCEPT
```
```
iptables -I INPUT 5 -p udp --dport smpt -j ACCEPT
```
```
iptables -I INPUT 5 -p tcp -s 192.168.1.1 --dport 22 -j  DROP
```     
```
iptables -I INPUT 4 -p tcp -s 192.168.1.12 --dport 24 -j REJECT
```
```
iptables -I INPUT 5 -p tcp -d 192.168.43.100 --dport 30 -j ACCEPT
```     
```
iptables -I INPUT 5 -p tcp --dport 21 -j REJECT
``` 
``` 
iptables -I INPUT 5  -p tcp --dport 80:90 -j REJECT
```
```     
iptables -I INPUT 1 -p tcp --dport telnet -j REJECT
```
```
iptables -I INPUT 5 -p udp --dport 53 -j REJECT
```
```     
iptables -I INPUT 5 -p udp --dport smpt -j REJECT
```
``` 
iptables -I INPUT 5 -p tcp --dport 21 -j DROP
```
```     
iptables -I INPUT 5  -p tcp --dport 80:90 -j DROP
```
```     
iptables -I INPUT 1 -p tcp --dport telnet -j DROP
```
```     
iptables -I INPUT 5 -p udp --dport 53 -j DROP
```
```     
iptables -I INPUT 5 -p udp --dport smpt -j DROP
```
**Temporary iptables changes permanent  save**
```     
serivce iptables save
``` 

**Permanent Configure.** 

-   **Edit Main Configuration File** 

    ```
    vim /etc/sysconfig/iptables
    ```
    ``` 
    systemctl restart iptables.service
    ```
