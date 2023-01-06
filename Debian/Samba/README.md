[SAMBA Client](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Debian/Samba/samba%20client.md)
# SMB Server
SMB (Server Message Block) is a network protocol used by Windows-based computers that allows the computer to share files, printers, and other resources with other computers on the network.

-   **Install SMB Server**
	```
	# apt install samba*
	```
    
	Configuration file
    ```
	# vim /etc/samba/smb.conf
	```	
-   **Port Allow in Iptables**
    ```
	# iptables -A INPUT -p tcp --dport 445 -j ACCEPT
	```	
	```
	# systemctl restart iptables
	```	
-   **Start SMB service**
	```
	# systemctl restart smbd.service
	```
    ```
	# systemctl enable smbd.service
	```
-   **Add User in SMB**
	```
	# smbpasswd -a Add_User_name
    ```

-	**Share Directory**

	*1. Make a share directory*
	```
	# mkdir /share_directory_name
	```
	*2. Change Directory Permission*
	```
	# chmod 777 /share_directory_name
	```
	*3. Edit configuration file*
	```
	# vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				comment	= display_name
				path = /path/to/sahre_directory
				available = yes
				browseable = yes
				read only = no

	*4. Start samba service.*

	```
	# systemctl restart smbd.service
	```
-	**Share Directory for valid users**

	*1. Make a share directory*
	```
	# mkdir /share_directory_name
	```
	*2. Change Directory Permission*
	```
	# chmod 777 /share_directory_name
	```
	*3. Edit configuration file*
	```
	# vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				comment	= display_name
				path = /path/to/sahre_directory
				available = yes
				browseable = yes
				read only = no
				valid users = users_name
	*4. Start samba service.*

	```
	# systemctl restart smbd.service
	```
-	**Share Directory for anonymous users**

	*1. Make a anonymous share directory*
	```
	# mkdir /anonymous_share_directory_name
	```
	*2. Change Directory Permission*
	```
	# chmod 777 /anonymous_share_directory_name
	```
	*3. Edit configuration file*
	```
	# vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				path = /path/to/anonymous_sahre_directory
				browseable = yes
				read only = no
				guest ok = yes

	*4. Start samba service.*
	```
	# systemctl restart smbd.service
	```
