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
## PROGRAM - SERVER ARP:
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
## PROGRAM - CLIENT ARP:
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
<img width="1919" height="1199" alt="Screenshot 2026-05-13 111410" src="https://github.com/user-attachments/assets/3038f323-7463-45a0-be3a-01ef102082db" />
<img width="1918" height="1195" alt="Screenshot 2026-05-13 111341" src="https://github.com/user-attachments/assets/cf3053cc-9db1-4b75-9d10-6a0284e55f37" />



## PROGRAM - SERVER RARP:
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
## PROGRAM - CLIENT RARP:
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
<img width="1919" height="1197" alt="Screenshot 2026-05-13 111635" src="https://github.com/user-attachments/assets/62e3785e-8630-4f67-b962-d497e44d2623" />
<img width="1919" height="1199" alt="Screenshot 2026-05-13 111616" src="https://github.com/user-attachments/assets/30c11342-b946-426c-aeb3-8cafc48bad1e" />
 
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
