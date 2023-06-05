# APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM

## EXP: 10

## DATE: 11-05-2023

## AIM:
To write a python program for creating Chat using TCP Sockets Links.

## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
server
4. Send and receive the message using the send function in socket.
## PROGRAM:
## CLIENT:
```python3
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
  print('receiving data...')
  data = s.recv(1024)
  print('data=%s', (data))
  if not data:
    break
  f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
  ```
## SERVER:
```python3
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'myfile.txt'  # Replace 'path/to' with the actual path to the file
    try:
        with open(filename, 'rb') as f:
            l = f.read(1024)
            while l:
                conn.send(l)
                print('Sent', repr(l))
                l = f.read(1024)
        print('Done sending')
    except FileNotFoundError:
        print(f'File {filename} not found.')
    
    conn.send('Thank you for connecting'.encode())
    conn.close()

```
   
## CLIENT OUTPUT : 

![client10](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EX-10/assets/119559905/5467a3cf-c9c8-49a8-9002-a3a67eee8279)


## SERVER OUTPUT :

![server10](https://github.com/BALUREDDYVELAYUDHAMGOWTHAM/EX-10/assets/119559905/af23d84d-e93e-42de-a20c-f8c131377ab0)


## RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was
successfully created and executed.
