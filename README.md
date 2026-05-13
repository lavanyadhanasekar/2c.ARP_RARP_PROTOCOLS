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
server
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
address = {"165.165.80.80":"6A:08:AA:C2", "165.165.79.1":"8A:BC:E3:FA"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

client
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    ip = input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address", s.recv(1024).decode())  # Added missing )
```
## OUPUT - ARP
<img width="1818" height="628" alt="Screenshot 2026-05-13 110512" src="https://github.com/user-attachments/assets/1beebd58-ffd6-4361-8378-fbab6d3adf30" />
<img width="1438" height="743" alt="Screenshot 2026-05-13 110530" src="https://github.com/user-attachments/assets/b0046251-f88d-405e-850c-197bd0dd2314" />

## PROGRAM - RARP
```
server
import socket
s = socket.socket()
s.bind(('localhost', 9000))
s.listen(5)
c, addr = s.accept()
address = {"6A:08:AA:C2":"192.168.1.100", "8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip = c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())

client
import socket
s = socket.socket()
s.connect(('localhost', 9000))
while True:
    ip = input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address", s.recv(1024).decode())
```
## OUPUT -RARP
<img width="1146" height="575" alt="Screenshot 2026-05-13 111225" src="https://github.com/user-attachments/assets/681cecbf-5d6e-4ade-95b7-b8f42cee3289" />
<img width="1564" height="652" alt="Screenshot 2026-05-13 111240" src="https://github.com/user-attachments/assets/01763a4f-13d9-4482-a5d3-61f445c4fb3b" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
