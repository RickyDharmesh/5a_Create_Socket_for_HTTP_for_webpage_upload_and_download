# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
client.py
```
import socket

# Create socket
c = socket.socket()

# Connect to server
c.connect(('localhost', 8080))

# Send HTTP request
request = "GET / HTTP/1.1"
c.send(request.encode())

# Receive response
data = c.recv(4096).decode()

print("Received Web Page:\n")
print(data)

# Close socket
c.close()
```
server.py
```
import socket

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for connection
s.listen(1)

print("Server waiting for connection...")

# Accept client connection
conn, addr = s.accept()
print("Connected by:", addr)

# Receive request from client
request = conn.recv(1024).decode()
print("Client Request:", request)

# Sample HTTP response
response = """HTTP/1.1 200 OK

<html>
<head><title>Web Page</title></head>
<body>
<h1>Welcome to HTTP Socket Programming</h1>
<p>Web page upload and download successful.</p>
</body>
</html>
"""

# Send response
conn.send(response.encode())

# Close connection
conn.close()
s.close()
```

## OUTPUT

UPLOAD:
<img width="1652" height="367" alt="Screenshot 2026-05-23 201638" src="https://github.com/user-attachments/assets/8ca90b2f-fe1f-4cae-bfe2-414dd276798c" />


DOWNLOAD:

<img width="1645" height="368" alt="Screenshot 2026-05-23 201652" src="https://github.com/user-attachments/assets/57cc3214-8a5c-4849-95a7-da23621a5fb6" />


## Result
Thus the socket for HTTP for web page upload and download created and Executed
