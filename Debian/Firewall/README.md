# What is Firewall.

A firewall is a network security system that monitors and controls incoming and outgoing network traffic based on predetermined security rules. A firewall can be hardware-based, software-based, or a combination of both.

# How firewalls are managed.
The **input**, **forward**, and **output** chains are all used to control and monitor traffic in a firewall, helping to protect the network or device from external threats and ensure that only authorized traffic is allowed to pass through.

## Firewall Configure.

**Install Firewall tools.**
```
# apt install iptables
```

```
# apt install iptables-persistent
```

**Start iptables service**
```
# systemctl start iptables.service
```
```
# systemctl enable iptebles.service
```

**Manage Table.**
```
# iptables --help
```		
```
# iptables -L
```				
```
# iptables -L -n --line-number
```
```
# iptables -n -L INPUT				
```
```	
# iptables -n -L OUTPUT
```		
```
# iptables -n -L FORWARD
```


**Permanent Configure.** 

- **Command Syntex**.

    ```
    # iptables -A Chain_Name -p tcp/udp --dport/--sport prot_number -j ACCEPT/REJECT/DROP
    ```
    ```
    # iptables-save > /etc/iptables/rules.v4
    ```

-   **Examples**

    ```
    # iptables -A INPUT -p tcp --dport 21 -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport 80:90 -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport telnet -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p udp --dport 3 -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p udp --dport smpt -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp -s 192.168.1.1 --dport 22 -j  DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp -s 192.168.1.12 --dport 24 -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp -d 192.168.43.100 --dport 30 -j ACCEPT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```	
    # iptables -A INPUT -p tcp --dport 21 -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport 80:90 -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport telnet -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p udp --dport 53 -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p udp --dport smpt -j REJECT
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport 21 -j DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport 80:90 -j DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT -p tcp --dport telnet -j DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT  -p udp --dport 53 -j DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
    ```
    # iptables -A INPUT  -p udp --dport smpt -j DROP
    # iptables-save > /etc/iptables/rules.v4
    ```
