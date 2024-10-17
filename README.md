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

## PROGRAM - ARP
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"165.165.79.1"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```
## OUPUT - ARP
### Client:

![Screenshot 2024-09-30 142857](https://github.com/user-attachments/assets/9adde38e-f87a-400b-9514-b8055a03e7b1)

### Server:

![Screenshot 2024-09-30 142910](https://github.com/user-attachments/assets/9649b779-7da3-47da-9d2f-11615c056c71)


## PROGRAM - RARP
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("not found".encode())
```
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("enter logical address:")
    s.send(ip.encode())
    print("mac address",s.recv(1024).decode())
```
## OUPUT -RARP
### Client:

![image](https://github.com/user-attachments/assets/54fc8e6f-5dc2-47f4-8082-7494e0cb5d9a)


### Server:

![image](https://github.com/user-attachments/assets/436ecbf1-7743-4a93-b668-fa7f8291678f)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.

