[Samba Client.](https://github.com/Mr-Secure-Code/Linux_Server/blob/main/Red%20HAT/Samba/samba%20client.md)
# SMB Server
SMB (Server Message Block) is a network protocol used by Windows-based computers that allows the computer to share files, printers, and other resources with other computers on the network.

-   **Install SMB Server**
	```
	yum install samba*
	```
    
	Configuration file
    ```
	vim /etc/samba/smb.conf
	```	
-   **Port Allow in Iptables**
    ```
	vim /etc/sysconfig/iptables
	```	
		-A INPUT -p tcp --dport 445 -j ACCEPT
	```
	systemctl restart iptables
	```	
-   **Start SMB service**
	```
	systemctl restart smb.service
	```
    ```
	systemctl enable smb.service
	```
-   **Add User in SMB**
	```
	smbpasswd -a Add_User_name
    ```

-	**Share Directory**

	*1. Make a share directory*
	```
	mkdir /share_directory_name
	```
	*2. Change Directory Permission*
	```
	chmod 777 /share_directory_name
	```
	*3. Edit configuration file*
	```
	vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				comment	= display_name
				path = /path/to/sahre_directory
				public = yes
				writable = yes
	*4. Start samba service.*

	```
	systemctl restart smb.service
	```
-	**Share Directory for valid users**

	*1. Make a share directory*
	```
	mkdir /share_directory_name
	```
	*2. Change Directory Permission*
	```
	chmod 777 /share_directory_name
	```
	*3. Edit configuration file*
	```
	vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				comment	= display_name
				path = /path/to/sahre_directory
				public = yes
				writable = yes
				valid users = users_name
	*4. Start samba service.*

	```
	systemctl restart smb.service
	```
-	**Share Directory for anonymous users**

	*1. Make a anonymous share directory*
	```
	mkdir /anonymous_share_directory_name
	```
	*2. Change Directory Permission*
	```
	chmod 777 /anonymous_share_directory_name
	```
	*3. change Directory user and group*
	```
	chown nobody:nobody anonymous_share_directory
	``` 
	*4. Edit configuration file*
	```
	vim /etc/samba/smb.conf
	```
	Go to end of this file and add this lines
		
		[share_directory_name]
				path = /path/to/anonymous_sahre_directory
				writable = yes
				guest ok = yes
				guest only = yes
				read only = no
				create mod = 0777
				directory mode = 0777
				force user = nobody
	*5. Start samba service.*
	```
	systemctl restart smb.service
	```
