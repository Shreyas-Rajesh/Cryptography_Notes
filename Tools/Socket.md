It is a python module that helps connect over network using: `TCP`, `UDP`

Import socket module -`import socket` 

1. `s = socket.socket(IPvX, TCP/UDP)`:
	- IPv4 - `socket.AF_INET`
	- TCP - `socket.SOCK_STREAM`
	- UDP - `socket.SOCK_DGRAM`

2. `server.bind(("0.0.0.0", 5555))` -  IP + PORT
3. `server.listen(1)` -  To listen for all connections
4. `conn, addr - server.accept()` - After connection established
5. `conn.recv()` -  To receive data (bytes)
6. `conn.send()` -  To send data (bytes)
7. `conn.close()` - To stop connection
8. 