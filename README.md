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
```
Client

socket 
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

```
Server

import socket 
s=socket.socket() 
s.connect(('localhost',8000)) 
while True: 
     ip=input("Enter logical Address : ") 
     s.send(ip.encode()) 
     print("MAC Address",s.recv(1024).decode())
 ```
## OUPUT - ARP

![WhatsApp Image 2024-10-08 at 08 18 22_b00f4d16](https://github.com/user-attachments/assets/9b3c81f6-aac9-41d9-8c4f-be532af0ce41)

![WhatsApp Image 2024-10-08 at 08 18 22_2ac0dca3](https://github.com/user-attachments/assets/6b1b2a57-9fe7-4e53-84b6-194d1be584cf)
## PROGRAM - RARP
```
Client

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
```
Server

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP

![WhatsApp Image 2024-10-08 at 08 18 23_ea279d6c](https://github.com/user-attachments/assets/f6ab4401-b516-4025-b556-6f1640ddb115)


![WhatsApp Image 2024-10-08 at 08 18 24_63b9af28](https://github.com/user-attachments/assets/61c517e9-27fd-4348-8308-494b73ff262f)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
