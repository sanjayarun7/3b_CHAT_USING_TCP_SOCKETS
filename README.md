# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
# cilent
```
# chat_client.py
import socket

# Step 1: Create a socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Step 2: Connect to server
client_socket.connect(('127.0.0.1', 65432))
print("Connected to server. Type 'bye' to exit.")

while True:
    # Send message to server
    msg = input("Client: ")
    client_socket.sendall(msg.encode())
    if msg.lower() == "bye":
        print("Chat ended by client.")
        break

    # Receive reply from server
    server_reply = client_socket.recv(1024).decode()
    if not server_reply or server_reply.lower() == "bye":
        print("Server disconnected.")
        break
    print("Server:", server_reply)

client_socket.close()
```
# server.py
```
# chat_server.py
import socket

# Step 1: Create a socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Step 2: Bind to localhost and port
server_socket.bind(('127.0.0.1', 65432))
server_socket.listen(1)

print("Server is listening on port 65432...")
conn, addr = server_socket.accept()
print(f"Connected by {addr}")

while True:
    # Receive message from client
    client_msg = conn.recv(1024).decode()
    if not client_msg or client_msg.lower() == "bye":
        print("Client disconnected.")
        break
    print("Client:", client_msg)

    # Send reply to client
    server_msg = input("Server: ")
    conn.sendall(server_msg.encode())
    if server_msg.lower() == "bye":
        print("Chat ended by server.")
        break

conn.close()
server_socket.close()
```
## OUPUT
<img width="1490" height="942" alt="image" src="https://github.com/user-attachments/assets/b26da64f-a03a-40f5-aec6-5207cc6c5387" />


## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
