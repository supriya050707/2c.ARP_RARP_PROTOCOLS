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

client
```
import socket

s=socket.socket()

s.bind(('localhost',8080))

s.listen(5)

c,addr=s.accept()

address={"10.255.144.126":"98-BD-80-D9-83-4D","10.136.126.196":"98-BD-80-DD-50-C2"};

while True:

      ip=c.recv(1024).decode()
      
      try:
      
          c.send(address[ip].encode())
          
      except KeyError:
      
          c.send("Not Found".encode())
```
server 
```

import socket

s=socket.socket()

s.connect(('localhost',8080))

while True:

  ip=input("Enter logical Address : ")

  s.send(ip.encode())

  print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP
client


<img width="576" height="112" alt="image" src="https://github.com/user-attachments/assets/dc65e7db-a49b-403e-81b3-5a94ededeee1" />


server

<img width="787" height="277" alt="image" src="https://github.com/user-attachments/assets/12318c16-493f-44e9-8480-135b5fe7e8b6" />

## PROGRAM - RARP

client
```
import socket

s=socket.socket()

s.bind(('localhost',8000))

s.listen(5)

c,addr=s.accept()

address={"98-BD-80-D9-83-4D":"10.255.144.126","98-BD-80-DD-50-C2":"10.136.126.196"};

while True:

      ip=c.recv(1024).decode()
      
      try:
      
          c.send(address[ip].encode())
          
      except KeyError:
      
          c.send("Not Found".encode())
```

server
```
import socket

s=socket.socket()

s.connect(('localhost',8000))

while True:

  ip=input("Enter MAC Address : ")

  s.send(ip.encode())

  print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
client


<img width="571" height="133" alt="image" src="https://github.com/user-attachments/assets/c2b3bbf9-c0bb-49b8-b9d8-af9a84dd0e96" />

server


<img width="588" height="212" alt="image" src="https://github.com/user-attachments/assets/a0d35ef4-a5af-4a01-b4d6-7595ad3b3b4e" />


## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
