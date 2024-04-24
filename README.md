# Ex.No:1b Study of chat application client server model

## Aim: 
To perform a study on Client Server Chat Applications.

## Algorithm:
# Server:
1. Create a server socket and bind it to port.
   
2. Listen for new connection and when a connection arrives, accept it.
   
3. Send server's date and time to the client.
   
4. Read client's IP address sent by the client.
   
5. Display the client details.
   
6. Repeat steps 2-5 until the server is terminated.
   
7. Close all streams.
   
8. Close the server socket.
   
9. Stop.
    
# Client:
1. Create a client socket and connect it to the server's port number.
   
2. Retrieve its own IP address using built-in function.

3. Send its address to the server.
   
4. Display the date & time sent by the server.
   
5. Close the input and output streams.
   
6. Close the client socket.
   
7. Stop.

## Introduction:
Client-server chat applications are a category of networked software that enables real-time communication between users over a network. This study explores the key components, architecture, and considerations in the development of client-server chat applications, highlighting their significance and common implementation practices.
Client-server chat applications are software systems that enable real-time communication between users over a network. These applications follow a client-server model, where one component (the server) manages connections and facilitates communication, while the other component (the client) interacts with the server to send and receive messages. Below are the fundamental aspects and components involved in the basics of client-server chat applications:

# 1. Client-Server Model:
# Server:
•	The server is a central component that listens for incoming connections from clients.

•	It manages the communication channels and facilitates the exchange of messages between clients.

•	It may handle user authentication, message routing, and other core functionalities.

# Client:
•	Clients are users or devices that connect to the server to participate in the chat.

•	Each client has a unique identity, often represented by a username.

•	Clients interact with the server to send and recieve messages.

# 2. Communication Protocols:
Communication between clients and servers often relies on established protocols. The choice of protocol influences the behavior of the chat application.

# TCP (Transmission Control Protocol):
•	Provides reliable, connection-oriented communication.

•	Ensures the ordered and error-free exchange of messages.

# UDP (User Datagram Protocol):
•	Connectionless and operates in a best-effort mode.

•	Faster but may result in message loss or disorder.

# 3. Socket Programming:
# Sockets:
•	Sockets serve as communication endpoints.

•	Each client and the server has a socket for sending and receiving data.

•	Functions: Socket programming involves functions for creating, binding, listening, accepting connections, and sending/receiving data through sockets.
 
# 4. User Authentication:
•	For security and privacy, chat applications often implement user authentication mechanisms.

•	Users are required to provide credentials (e.g., username and password) to access the chat system.

•	More advanced methods like tokens or secure protocols can enhance authentication.

# 5. Message Routing:
•	The server is responsible for routing messages from one client to another.

•	It ensures that messages are delivered to the intended recipients.

•	Message routing may involve maintaining a list of connected users and their associated sockets.

## Architecture:
# Client-Server Model:
Client-server chat applications typically follow the client-server model, where one entity acts as the server, managing connections and facilitating communication, and one or more entities act as clients, initiating communication with the server.

# Communication Protocols:
The choice of communication protocol is crucial. Many chat applications use TCP (Transmission Control Protocol) for reliable, connection-oriented communication to ensure the ordered and error-free exchange of messages.

# User Authentication:
User authentication mechanisms are essential to ensure secure and authorized access to the chat system. This can involve username-password authentication or more advanced methods like tokens.

## Components of Client-Server Chat Applications:
# Server-Side Components:
•	Socket Handling: The server manages incoming client connections using sockets, creating a separate thread or process for each connected client.

•	User Management: Maintaining information about connected users, their status, and handling login/logout functionality.

•	Message Routing: Implementing logic to route messages from one client to another, ensuring proper delivery.

## Considerations in Development:
# 1.	Concurrency and Multithreading:
Chat applications often require handling multiple connections simultaneously. The server must be designed to support concurrency, commonly achieved through multithreading or asynchronous programming.

# 2.	Security:
Ensuring the security of user data and messages is paramount. Encryption techniques, such as SSL/TLS, can be implemented to secure data in transit. Proper user authentication mechanisms help prevent unauthorized access.

# 3.	Scalability:
As the number of users grows, the chat application must be scalable. This involves optimizing server-side architecture to handle increasing loads efficiently.

# 4.	Persistence:
Some chat applications implement message persistence, allowing users to retrieve past messages. This may involve using databases to store and retrieve chat history.

# 5.	Notification Systems:
Implementing real-time notifications to inform users of new messages, user presence changes, or other relevant events.

Client-server chat applications are versatile tools that facilitate real-time communication between users over a network. They incorporate various components, including server-side and client-side elements, and must consider factors such as security, scalability, and concurrency. As technology continues to advance, client-server chat applications remain integral for collaborative communication in various domains.

Client-server chat applications are foundational to real-time communication over networks. They incorporate principles of socket programming, communication protocols, and security mechanisms to provide a seamless user experience. Understanding the basics of client-server chat applications is essential for developers involved in networked application development, as they form the backbone of various collaborative communication systems. As technology evolves, chat applications continue to adapt, incorporating new features and technologies to enhance user interaction and connectivity.

## Program:
# Client
~~~
import socket
from datetime import datetime
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
print("client address:",addr)
now=datetime.now()
c.send(now.strftime("date:%d/%m/%Y & time:%H:%M:%S").encode())
ack=c.recv(1024).decode()
if ack:
    print(ack)
    c.close()
~~~

# Server
~~~
import socket
s=socket.socket()
s.connect(('localhost',8000))
print(s.getsockname())
print(s.recv(1024).decode())
s.send("acknowledgement received from the server".encode())
~~~

## Output:
# Client
![image](https://github.com/K-Dharshini/ChatStudy/assets/139334830/c1e36037-c9b8-4886-810e-893510874f23)

# Server
![image](https://github.com/K-Dharshini/ChatStudy/assets/139334830/fa77e9ca-a193-4666-89dc-7fe0f17cb3cc)

## Result:
Thus the study on Client Server Chat Applications has been performed.
