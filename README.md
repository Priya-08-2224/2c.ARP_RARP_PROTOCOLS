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
## CLIENT
```
 
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
## SERVER
```
 
import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True:
    ip=input("Enter logical Address : ") 
    s.send(ip.encode()) 
    print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
## CLIENT
![Screenshot 2025-04-12 232442](https://github.com/user-attachments/assets/cbce58ac-4775-4f29-8195-306cd7480a9b)
## SERVER
![Screenshot 2025-04-12 232356](https://github.com/user-attachments/assets/cb513940-e694-447f-b777-531a4bab77ef)

## PROGRAM - RARP
## CLIENT
```
 
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
## SERVER
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode()) 
```
## OUPUT -RARP
## CLIENT
![Screenshot 2025-04-13 010649](https://github.com/user-attachments/assets/54d9ff96-431f-480e-bac2-cd65a399f3cf)
## SERVER
![Screenshot 2025-04-13 010731](https://github.com/user-attachments/assets/ce8195d0-5f35-42d3-9f56-77903ff34be7)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
