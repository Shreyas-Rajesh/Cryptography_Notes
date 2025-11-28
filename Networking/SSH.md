Before SSH people used telnet to connect to a remote machine, the problem with these connections was that they transmitted information in plaintext. SSH solved the problem by encrypting the connection. 

![[SSH_1.png]]

With an SSH connection the person sniffing the packets wont be able to see what the packets are but they will see the frequency and that packets are being sent.

So when initiating a SSH connection the first things that happens is TCP connection is established. (default port is 22)

Packet form:
- Packet length - 4bytes in size (how big the packet is)
- Padding - 1 byte (how much padding the packet will have)
- Payload - actual data (size varies)
- Padding (to align data according to encryption)
- MessageAuthentication Code (tag) - to verify the authenticity of the data
Some form of compression is applied. 
When the message is read by others all they can see the packet-length and message auth, the other things are encrypted.
The encryption used when sending packets are decided by the server and client.

There are 2 types of keys while connecting over SSH:
- Public key
- Private key (.pem file is a container format that may include just the public certificate or may include an entire certificate chain including public key, private key, and root certificates.)

## SSH process
#### TCP connection
SYN (to initialise connection) -> SYN/ACK -> ACK (Acknowledge)

#### Protocol Exchange
Server sends their ssh protocol version and then the client

#### Key Exchange
Client and Server agrees on a type of encryption and other things. 
They then perform a **Diffie–Hellman or elliptic-curve key exchange** to generate a shared session key. This session key encrypts all future traffic.

#### Server Authentication
Server proves who it is, by showing the host key

#### User authentication
Password Authentication - The password is encrypted by the session key.
OR
Public Key Authentication - 
- Server sends challenge
- Client signs challenge with private key
- Server checks signature using the public key

## To start a SSH port
`sudo systemctl start ssh` - This opens a SSH port on your device
`systemctl status` - To see if SSH port is open or not, it also shows which port is listening.
`sudo systemctl restart ssh` - To restart ssh 
`sudo systemctl stop ssh` - to stop ssh

### To Connect
`ssh username@host -p <port>` - to connect to a specific port (optional).
`ssh -i ~/.ssh/id_rsa username@host` - to connect using a specific private key file.

### To copy files
`scp file.txt username@host:/path/` - To upload
`scp username@host:/path/file.txt .` - To download

### To generate ssh keys
`ssh-keygen -t Type` -  to create a key pair (type is optional)

### To add public key to server
`ssh-copy-id username@host` 
this adds the public key at the point - `~/.ssh/authorized_keys`



