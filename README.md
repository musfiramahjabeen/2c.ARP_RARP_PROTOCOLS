# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
```python
import socket
s=socket.socket()
s.bind(('localhost',8880))
s.listen(5)
c,addr=s.accept()
address={"192.168.3.14":"E0-2E-0B-7A-73-08"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
## OUPUT - ARP
![Screenshot 2024-10-17 183256](https://github.com/user-attachments/assets/d988fb78-91fc-4845-ad22-f66805d82825)

## PROGRAM - RARP
```python
import socket
s=socket.socket()
s.connect(('localhost',8880))
while True:
    ip=input("Enter Logical Address:")
    s.send(ip.encode())
    print("MAC address",s.recv(1024).decode())
```
## OUPUT -RARP
![Screenshot 2024-10-17 183311](https://github.com/user-attachments/assets/7315d86f-7f9e-4e04-8c84-d862532be412)
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
