# 2c.SIMULATING ARP /RARP PROTOCOLS
```
NAME: THEJASHREE S
REG NO: 212224240175
```
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
Client program:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode()) 
```
Server program:
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
## OUPUT - ARP

Client output:

<img width="731" height="268" alt="image" src="https://github.com/user-attachments/assets/9e947bdc-d280-4ddc-9a8a-9d80628d3593" />

Server output:

<img width="766" height="173" alt="image" src="https://github.com/user-attachments/assets/d648e094-8c98-4d9e-819e-4792a1911aab" />

## PROGRAM - RARP
Client program:
```python
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address", s.recv(1024).decode())  
```
Server program:
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
## OUPUT -RARP

Client output:

<img width="921" height="336" alt="image" src="https://github.com/user-attachments/assets/bb899d9b-12c9-4ada-8451-3d3031fbbc6d" />

Server output:

<img width="748" height="285" alt="image" src="https://github.com/user-attachments/assets/ce5ade4e-c825-49a6-a860-aec231bd28ba" />

## RESULT
Thus, the python program for simulating ARP/RARP protocols using TCP was successfully executed.
