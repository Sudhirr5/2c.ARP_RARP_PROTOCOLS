# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP/RARP protocols using TCP.
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
```
Developed by : SUDHIR KUMAR .R
Register by : 212223230221
```
### CLIENT :
```python
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
### SERVER :
```python
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
### CLIENT :

![exp5-1](https://github.com/Sudhirr5/2c.ARP_RARP_PROTOCOLS/assets/139332214/f9ace9d6-fa00-4e97-8003-27d8a376309e)

### SERVER :

![exp5-2](https://github.com/Sudhirr5/2c.ARP_RARP_PROTOCOLS/assets/139332214/fdda0243-549e-4e3d-b6c3-113fb2f56a60)

## PROGRAM - RARP
```
Developed by : SUDHIR KUMAR .R
Register by : 212223230221
```
### CLIENT :
```python
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
### SERVER :
```python
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
   ip=input("Enter MAC Address : ")
   s.send(ip.encode())
   print("Logical Address",s.recv(1024).decode())

```
## OUPUT -RARP
### CLIENT :

![exp5-3](https://github.com/Sudhirr5/2c.ARP_RARP_PROTOCOLS/assets/139332214/21bff16f-7437-4066-997c-d7775bda9730)

### SERVER :

![exp5-4](https://github.com/Sudhirr5/2c.ARP_RARP_PROTOCOLS/assets/139332214/ea176810-6728-4ff4-9576-e709c77b2a35)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
