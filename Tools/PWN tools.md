To install pwntools : `pip install pwntools`
Import module : `pwn`
Create a process object/tube : 
	`f = process("path_to_binary")` to open a local binary
	`f = remote("domain/ip,port_number)`to connect to a remote server. (add an argument `ssl = True` if SSL is used)
To kill a process : `kill()`
To receive data:
	1. `recv(n)` - receives 'n' bytes (byte values)
	2. `recvS(n)` - receives 'n' bytes (string value)
	3. `recvb(s)` - receive 'n' bytes (bytearray)
	4. `recvall()` - to receive until newline character
			1.`timeout = 1` use this for timing out the receive
		Note there is `recvallS` and `recvallb
	5.  `recvline()` - to receive one line (waits for "\n")
	6. `recvline_endswith(delimiter)` - goes line by line till reaching the delimiter and returns the line with the delimiter
	7. `recvuntil(delimiter)` - receives a stream of data (from start to end) till encountering the delimiter.
	8. `recvregex(regex)` - Receive up to and including something that matches regex
	9. `recvlines(n)` - receives "n" lines

To send data:
	1. `send(s)` - to send the bytes "s"
	2. `sendafter(delimiter,data,timeout(optional)` -  to send data after it encounters the delimiter
	3. `sendline(s)` - send the data with a newline char at the end.
		Note there is `sendlineafter`
To interact with the binary (also used to not close the binary): `interactive()` 
To set all values automatically in context variable : `pwn.context.binary = path_to_binary`
To set the architecture : `pwn.context.arch = "amd64"`
To log all traffic  : `pwn.context.log_level = "debug"`
To set up the operating system : `pwn.context.os = "linux"`
