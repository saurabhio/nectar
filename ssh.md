### SSH

  ```
  There are a number of SSH clients available both free and commercial, with OpenSSH being the most widely used client.  
  The OpenSSH client program is called ssh and can be invoked from the terminal. The OpenSSH client package 
  also provides other SSH utilities such as scp and sftp that are installed alongside the ssh command.
  
  sudo apt update
  sudo apt install openssh-server openssh-client
  
  nc -vz 127.0.0.1 22
  sudo /etc/init.d/ssh restart
  or
  sudo service ssh restart

  Each host has a unique fingerprint that is stored in the ~/.ssh/known_hosts file.
  
  When the username is not given, the ssh command uses the current system login name.
  
  To connect on a non-default port, use the -p option to specify the port:

  ssh -p 5522 username@hostname
  
  The OpenSSH client reads the options set in the per-user configuration file (~/.ssh/config). 
  A sample SSH config is shown below:

  Host dev
    HostName dev.linuxize.com
    User mike
    Port 4422

  now
  ssh dev
  means ssh -p 4422 mike@dev.linuxize.com

  If you already don't have SSH key pair on your local machine you can generate one by typing:

  ssh-keygen -t rsa -b 4096 -C "your_email@domain.com"

  Once you have your key pair, copy the public key to the remote server:

  ssh-copy-id username@hostname

  Enter the remote user password, and the public key will be appended to the remote user authorized_keys file.

  Once the key is uploaded, you can log in to the remote server without being prompted for a password.


  SSH tunneling or SSH port forwarding is a method of creating an encrypted SSH connection between a client 
  and a server machine through which services ports can be relayed.

  There are three types of SSH port forwarding:
    Local Port Forwarding
    Remote Port Forwarding
    Dynamic Port Forwarding

  Local Port Forwarding
  Local port forwarding allows you to forward a connection from the client host to the SSH server host and then to the destination host port. 
  Local port forwarding allows you to forward a port on the local (ssh client) machine to a port on the remote (ssh server) machine, which is then forwarded to a port on the destination machine.
  
  In this type of forwarding the SSH client listens on a given port and tunnels any connection to that port to the specified port on the remote SSH server, which then connects to a port on the destination machine. The destination machine can be the remote SSH server or any other machine.


  ssh -L [LOCAL_IP:]LOCAL_PORT:DESTINATION_HOST:DESTINATION_PORT -N -f [USER@]SSH_SERVER
  The -f option tells the ssh command to run in the background and -N not to execute a remote command.
  
  Remote Port Forwarding

  Remote port forwarding is the opposite of local port forwarding. It forwards a port from the server host to the client host and then to the destination host port. 
  Remote port forwarding is the opposite of local port forwarding. It allows you to forward a port on the remote (ssh server) machine to a port on the local (ssh client) machine, which is then forwarded to a port on the destination machine. 
  
  In this type of forwarding the SSH server listens on a given port and tunnels any connection to that port to the specified port on the local SSH client, which then connects to a port on the destination machine. The destination machine can be the local or any other machine.

  ssh -R [REMOTE:]REMOTE_PORT:DESTINATION:DESTINATION_PORT -N -f [USER@]SSH_SERVER

  Dynamic Port Forwarding

  Dynamic port forwarding creates a SOCKS proxy server that allows communication across a range of ports.
  Dynamic port forwarding allows you to create a socket on the local (ssh client) machine which acts as a SOCKS proxy server. 
  When a client connects to this port the connection is forwarded to the remote (ssh server) machine, which is then forwarded to a dynamic port on the destination machine.

  This way, all the applications using the SOCKS proxy will connect to the SSH server and the server will forward all the traffic to its actual destination.

  To create a dynamic port forwarding (SOCKS) pass the -D option to the ssh client:

  ssh -R [LOCAL_IP:]LOCAL_PORT  -N -f username@hostname

  scp local-file.txt remote_user@remote_server:/home/remote_user/xyz 

  scp -rp /path/to/source/.  remote_user@remote_server:/path/to/dest/
  
  recommended way:
  rsync -avzP /path/to/source/ remote_user@remote_server:/path/to/dest/

  scp remote_user@remote_server:/home/remote_user/xyz.tar /home/local_user/Desktop
  
  

   scp -i key_file.pem remote_user@remote_server:/remote/dir/foobar.txt /local/dir
   scp foobar.txt remote_user@remote_server:/some/remote/directory

   cp user1@remote1:/some/remote/directory/foobar.txt user2@remote2:/some/remote/directory/
   
   ```
  
