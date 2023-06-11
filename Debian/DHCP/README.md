# DHCP Server / DHCP (Dynamic Host Configuration Protocol)

<font size=5> <span style="color: white;">
DHCP Server is IP distribution. Here IP uses Dora process to distribute.
</font></span>


#  <span style="color: RED;"> DORA Process </span>

<font size=5> <span style="color: white">
DORA stands for Discovery, Offer, Request, and Acknowledge. It is the process that a DHCP server uses to assign an IP address to a device that is connecting to a network.

<span style="color: white">

Here is a brief summary of the DORA process:

**Discovery:** When a device connects to a network, it broadcasts a message on the network asking if there are any DHCP servers available.

**Offer:** If there is a DHCP server on the network, it responds to the device with an offer of an IP address that the device can use.

**Request:** The device then sends a request to the DHCP server, asking to be assigned the IP address that was offered.

**Acknowledge:** The DHCP server then acknowledges the request and assigns the IP address to the device. The device can now use the assigned IP address to communicate with other devices on the network.

</font></span>

# DHCP Configuration.

-   **Install DHCP.**

    ```
    apt instal isc-dhcp-server
    ```

-   **Allow Your Enterface name.**
    ```
    vim /etc/default/isc-dhcp-server
    ```
    
-   **Start DHCP Service.**
    ```
    systemctl enable isc-dhcp-server.service
    ```
    ```
    systemctl start isc-dhcp-server.service
    ```

-   **DHCP Configure**.

    ```
    vim /etc/dhcp/dhcp.config
    ```

    Distribute IP address.
    ```
    Note:- Search # authoritative And Uncomment authoritative.
    authoritative;

    Uncomment This Lines.

    Lines Syntex.

        subnet Enter_Network_IP_Subnet netmask 255.255.255.0 {
        range Start_IP END_IP;
        option routers Enter__your_Gateway;
    }
    ```

    Expulsion/Excluded IP Address.

    ```
    Note:- Search # authoritative And Uncomment authoritative.
    authoritative;

    Uncomment This Lines.

    Lines Syntex.

        subnet Enter_Network_IP_Subnet netmask 255.255.255.0 {
        range Start_IP END_IP;

        range Start_IP End_IP;
        option routers Enter__your_Gateway;
    }
    ```

    Reserved IP address.

    ```
    Note:- Search # authoritative And Uncomment authoritative.
    authoritative;

    Uncomment This Lines.
    Lines Syntex.

        subnet Enter_Network_IP_Subnet netmask 255.255.255.0 {
        range Start_IP END_IP;
        option routers Enter__your_Gateway;
    }

    Uncomment This Lines.
    Lines Syntex.

    host fantasia {
    hardware ethernet Enter_Reserved_Mac_Address;
    fixed-address Enter_Fixed_IP;
    }
