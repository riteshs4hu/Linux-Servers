# SSH Server.
SSH is often used to remotely access and manage servers, as it provides a secure and encrypted connection over the internet. It is also commonly used to securely transfer files between computers.

# SSH Client tool.

-   **Install Client Tool.**
    ```
    apt install openssh-clients
    ```
-   **ssh connection using with ip.**
    ```
    ssh username@remote_system_address
    ```
-   **ssh connection using with port and ip.**
    ```
    ssh -p port_number username@remote_system_address
    ```
-   **ssh connation using with public key.**
    ```
    ssh -i id_rsa user@remote_system_address
    ```
# SSH Server.

-   **Install SSH Server.**
    ```
    apt install openssh-*
    ```
-   **Start SSH Service.**
    ```
    systemctl enable ssh.service
    ```
    ```
    systemctl start ssh.service
    ```
    
-   **SSH Configure with specific port.**

    *Open main Configuration file.*
    ```
    vim /etc/ssh/sshd_config
    ```
    *Search **'# port22'** remove the **'#'** to uncomment the directive.*
    ```
    PORT Enter_Specific_port
    ```
    *Restart the SSH server to apply the changes.*
    ```
    systemctl restart ssh.service
    ```
-   **SSH Configure with specific IP.**

    *Open main Configuration file.*
    ```
    vim /etc/ssh/sshd_config
    ```
    *Search **'#ListenAddress 0.0.0.0'** remove the **'#'** to uncomment the directive.*
    ```
    ListenAddress Enter_Specific_IP
    ```
    *Restart the SSH server to apply the changes.*
    ```
    systemctl restart ssh.service
    ```
-   **Disable root login in SSH.**

    *Open main Configuration file.*
    ```
    vim /etc/ssh/sshd_config
    ```
    *Search ```PermitRootLogin yes```And convert with ```PermitRootLogin no```*
    
    *Restart the SSH server to apply the changes.*
    ```
    systemctl restart ssh.service
    ```
-   **SSH Configure using with public key.**
    
    **Edit Configuration File**

    *Open File.*
    ```
    vim /etc/ssh/sshd_config
    ```

    *1. Search :- ```# PubkeyAuthentication yes``` Replace with ```PubkeyAuthentication yes```*
    
    *2. Search :- ```PasswordAuthentication yes``` Replace with ```PasswordAuthentication no```*

    **Go to the user you want to access remotely and run this command.**
    ```
    ssh-keygen -f path/to/new_ssh_key_filename
    ```
    ```
    ssh-keygen
    ```
            Enter folder name in which to save the key (/home/user/.ssh/id_rsa):
            Enter password (empty for no passphrase):
            Enter same password again:
    ```
    cd .ssh
    ```
    ```
    mv id_rsa.pub authorized_keys
    ```
    Send public key in remote server.
    ```
    scp ~/.ssh/id_rsa user@remote-server:
    ```
    *Restart the SSH server to apply the changes.*
    ```
    systemctl restart ssh.service
    ```
