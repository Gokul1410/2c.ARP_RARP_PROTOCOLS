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

## OUPUT - ARP

![311533489-4c2ecb21-8a9e-4b32-b2b9-3745147a6c68](https://github.com/Gokul1410/2c.ARP_RARP_PROTOCOLS/assets/153058321/5965f160-4056-45e0-a425-b19e452c5fc3)

## PROGRAM - RARP

### Server

import socket

s=socket.socket()

s.connect(('localhost',8000))


while True:

    ip=input("Enter logical Address : ")
    
    s.send(ip.encode())
    
    print("MAC Address",s.recv(1024).decode())

## OUPUT -RARP
![311533680-07784046-8105-4452-aa8d-59ee66189c04](https://github.com/Gokul1410/2c.ARP_RARP_PROTOCOLS/assets/153058321/362adbdd-6841-41e6-bc98-2d83f80f80f9)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
