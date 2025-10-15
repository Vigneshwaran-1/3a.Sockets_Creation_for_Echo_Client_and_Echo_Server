# 3a.CREATION FOR ECHO CLIENT AND ECHO SERVER USING TCP SOCKETS
# AIM
To write a python program for creating Echo Client and Echo Server using TCP
Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server .
4. Send and receive the message using the send function in socket.
## PROGRAM

At server
~~~~
import socket
HOST = '127.0.0.1'   
PORT = 65432         

server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server_socket.bind((HOST, PORT))
server_socket.listen()
print(f"Server is listening on {HOST}:{PORT}...")

conn, addr = server_socket.accept()
print(f"Connected by {addr}")

while True:
    data = conn.recv(1024) 
    if not data:
        break  
    print(f"Received: {data.decode()}")
    conn.sendall(data) 
conn.close()
server_socket.close()
print("Server closed.")
~~~~

At client 
~~~~
import socket

HOST = '127.0.0.1'
PORT = 65432

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client_socket.connect((HOST, PORT))
print("Connected to server.")
while True:
    message = input("Enter message (type 'exit' to quit): ")
    if message.lower() == 'exit':
        break
    client_socket.sendall(message.encode())  
    data = client_socket.recv(1024)        
    print(f"Echo from server: {data.decode()}")

client_socket.close()
print("Connection closed.")
~~~~
## OUPUT
At server

<img width="1224" height="466" alt="Screenshot 2025-10-15 102429" src="https://github.com/user-attachments/assets/4e13e682-0b74-4fec-bdc7-d414784a544c" />

At client


<img width="1223" height="561" alt="Screenshot 2025-10-15 102445" src="https://github.com/user-attachments/assets/d4ebb53f-11cf-492b-ab6a-a4d18c513ec6" />




## RESULT
Thus, the python program for creating Echo Client and Echo Server using TCP Sockets Links 
was successfully created and executed.
