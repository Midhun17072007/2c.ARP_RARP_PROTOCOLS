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
### Client:
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server:
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
### Client:
<img width="444" height="88" alt="image" src="https://github.com/user-attachments/assets/865c7143-3f9e-4019-980d-b616216198be" />

### Server:
<img width="430" height="184" alt="image" src="https://github.com/user-attachments/assets/ebd4cffd-9dc9-42e5-9f60-02e0f660f1c9" />


## PROGRAM - RARP
### Client:
```py
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

```
### Server:
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())


```
## OUPUT -RARP
### Client:

<img width="420" height="105" alt="image" src="https://github.com/user-attachments/assets/f7421432-bfb6-40f6-826b-c8540234d9b4" />


### Server:

<img width="408" height="223" alt="image" src="https://github.com/user-attachments/assets/d34ac4df-ecce-4684-b11c-3f211bf1f9e0" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
