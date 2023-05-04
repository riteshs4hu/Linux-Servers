# SAMBA Clients.

-   **Install Client Tool.**
    ```
    apt install smbclient
    ```
-   **Client Tools.**

    **1. smbclient**
    
    The smbclient command is a command-line utility that allows you to interact with SMB servers. You can use it to list the available shares on a server, get files from a server, and put files onto a server.

    ```
    smbcliet -L //IP -U enter_user_name
    ```
    ```
    smbclient -L //IP -U "" -N										
    ```
    ```
	smbclient //IP/data access_folder_name -U enter_user_name
	```
		-U		Set the network username
		-L		Get a list of shares available on a host
		-N		NULL 
    
    **2. smbget**

    The smbget command is a utility for retrieving files from an SMB server. You can use it to download a file from a server by specifying the server URL and the path to the file you want to download.
	
    ```
    smbget -U enter_user_name smb://IP/data_folder_name/file_access_name
	```
	**3. smbtar**					

    The smbtar command is a utility for creating tar archives of files and directories on an SMB server. You can use it to download a directory from a server by specifying the server, share name, username, password, and the name of the tar archive file you want to create.
	
		-s		Server
		-x		Folder Share Name
		-u		Username
		-p		Password
		-t		New Tar File name 
		-v		Verbose mode
	
	**4. Temporary Mount**
	```	
	mount -t cifs -o username=user,password=user_password //IP/Data_Access_folder /mount_folder_name
	```
		-t 		Type
		-o		Options
