# DHCP Server / DHCP (Dynamic Host Configuration Protocol)

<font size=5> <span style="color: white;">
DHCP Server is IP distribution. Here IP uses Dora process to distribute.
</font></span>


#  <span style="color: RED;"> DORA Process </span>

<font size=5> <span style="color: white">
DORA stands for Discovery, Offer, Request, and Acknowledge. It is the process that a DHCP server uses to assign an IP address to a device that is connecting to a network.

<span style="color: white">

Here is a brief summary of the DORA process:

Discovery: When a device connects to a network, it broadcasts a message on the network asking if there are any DHCP servers available.

Offer: If there is a DHCP server on the network, it responds to the device with an offer of an IP address that the device can use.

Request: The device then sends a request to the DHCP server, asking to be assigned the IP address that was offered.

Acknowledge: The DHCP server then acknowledges the request and assigns the IP address to the device. The device can now use the assigned IP address to communicate with other devices on the network.

</font></span>

# DHCP Configuration.

-   **Install DHCP.**

    ```
    # yum instal dhcp*
    ```

-   **Start DHCP Service.**
    ```
    # systemctl enable dhcpd.service
    ```
    ```
    # systemctl start dhcpd.service
    ```

-   **Allow DHCP port on firewall.**

    ```
    # iptables -A INPUT -p udp --dport 67 -j ACCEPT
    ```
    ```
    # iptables-save
    ```
-   **Configuration DHCP.**

    ```
    # vim /etc/dhcp/dhcp.config
    ```
    Distribute IP address.
    ```
    authoritative;

        # specify network address and subnet mask
        subnet 192.168.43.0 netmask 255.255.255.0 {
        # specify the rang of lease IP address
        range 192.168.43.100 192.168.43.150;
        # DNS server for name resolution
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        # specify routers gateway
        option routers 192.168.43.1;
        # specify bordcast address
        option broadcast-address 192.168.43.255;
        # default lease time
        default-lease-time 600;
        # max lease time
        max-lease-time 7200;
        }
    ```

    Expulsion/Excluded IP Address.

    ```
    authoritative;

        # specify network address and subnet mask
        subnet 192.168.43.0 netmask 255.255.255.0 {
        # specify the rang of lease IP address
        range 192.168.43.10 192.168.43.50;
        range 192.168.43.100 192.168.43.150;
        # DNS server for name resolution
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        # specify routers gateway
        option routers 192.168.43.1;
        # specify bordcast address
        option broadcast-address 192.168.43.255;
        # default lease time
        default-lease-time 600;
        # max lease time
        max-lease-time 7200;
        }
    ```

    Reserved IP address.

    ```
    authoritative;

        # specify network address and subnet mask
        subnet 192.168.43.0 netmask 255.255.255.0 {
        # specify the rang of lease IP address
        range 192.168.43.10 192.168.43.50;
        range 192.168.43.100 192.168.43.150;
        # DNS server for name resolution
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        # specify routers gateway
        option routers 192.168.43.1;
        # specify bordcast address
        option broadcast-address 192.168.43.255;
        # default lease time
        default-lease-time 600;
        # max lease time
        max-lease-time 7200;
        }
        
    host hostname/anyname {hardware ethernet Reserved_IP_address_Macaddress; fixed-address 192.168.43.10;}
    ```

    Blacklist IP Address.

    ```
    authoritative;

        # specify network address and subnet mask
        subnet 192.168.43.0 netmask 255.255.255.0 {
        # specify the rang of lease IP address
        range 192.168.43.10 192.168.43.50;
        range 192.168.43.100 192.168.43.150
        # DNS server for name resolution
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        # specify routers gateway
        option routers 192.168.43.1;
        # specify bordcast address
        option broadcast-address 192.168.43.255;
        # default lease time
        default-lease-time 600;
        # max lease time
        max-lease-time 7200;
        }
        
    host anynaem {hardware ethernet Black_IP_Address_Macaddress; deny booting;}
    ```

    Whitelist IP Address.

    ```
    authoritative;

        # specify network address and subnet mask
        subnet 192.168.43.0 netmask 255.255.255.0 {
        # specify the rang of lease IP address
        range 192.168.43.10 192.168.43.50;
        range 192.168.43.100 192.168.43.150;
        # DNS server for name resolution
        option domain-name-servers 8.8.8.8, 8.8.4.4;
        # specify routers gateway
        option routers 192.168.43.1;
        # specify bordcast address
        option broadcast-address 192.168.43.255;
        # default lease time
        default-lease-time 600;
        # max lease time
        max-lease-time 7200;
        dny unknow-clients;
        }

    host anynaem {hardware ethernet macaddress;}
    ```
