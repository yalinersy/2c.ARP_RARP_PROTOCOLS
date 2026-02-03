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
## Server
```
import socket
import datetime

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server waiting for connection...")

while True:
    c, addr = s.accept()
    print("Connected from:", addr)

    now = datetime.datetime.now()
    c.send(str(now).encode())

    msg = c.recv(1024).decode()
    print("Client Message:", msg)

    c.close()

```
## OUPUT - ARP
## Server
<img width="722" height="100" alt="image" src="https://github.com/user-attachments/assets/7710e91b-a2ae-4e9d-ab9f-e828b1bdb5f9" />

## PROGRAM - RARP
## Client
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

print(s.getsockname())
print(s.recv(1024).decode())

s.send("Acknowledgement received from the server".encode())
s.close()

```
## OUPUT -RARP
## Client
<img width="604" height="84" alt="image" src="https://github.com/user-attachments/assets/e38d7509-f597-4d45-a6b5-ce1078057934" />

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
