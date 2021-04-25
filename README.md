## Chatroom

This is a simple TCP chatroom program created using python. It creates a simple TCP server socket and accepts connections. Once a connection is accepted, it listens for new input lines and echo's them back to the client.

For this program, I used the client-server architecture. This means that we will have multiple clients (the users) and one central server that hosts everything and provides the data for these clients. Therefore, two Python scripts had to be written. One is for starting the server and one is for the client. We have to run the server first, so that there is a chat, which the clients can connect to.

### Server's Script

For this script, we need to import two libraries, **socket and threading**. Socket is used for the network connection and threading is necessary for performing various tasks at the same time.

The next task is to define the connection data and to initialize our socket. We need an IP-address for the host and a free port number for our server. In this script, I used the localhost address (127.0.0.1) and the port 55555.

When defining the socket, we need to pass two parameters. These define the type of socket we are using. The first one (AF_INET) indicates that we are using an internet socket rather than an unix socket. The second parameter stands for the protocol we are using. SOCK_STREAM indicates that we are using TCP and not UDP.

After defining the socket, we bind it to our host and the specified port by passing a tuple that contains both values. We then put our server into listening mode, so that it waits for clients to connect. At the end we create two empty lists to store the connected clients and their nicknames.

Here we define a little function that is going to help us broadcasting messages. What it does is just sending a message to each client or user that is connected. Now we implement the first major function. This function is responsible for handling messages from the clients. And last but not least, we execute the receive function. It also starts an endless while-loop which constantly accepts new connections from clients. After that it waits for a response (which contains the nickname) and appends the client with the respective nickname to the lists. Finally, we start a new thread that runs the previously implemented handling function for this particular client and our server is done.

### Client's Script

For this script, we need to import the same libraries again. The first steps of the clients are to choose a nickname and to connect to our server. We need to know the exact address and the port at which our server is running.

The client has two threads that are running at the same time. The first one constantly receives data from the server and the second one sends messages to the server. So we need two functions here.

firstly, the recieve function. Here we have an endless while-loop. It constantly tries to receive messages and to print them onto the screen.

Secondly, we define a function for sending messages. The write function is a short one. It also runs in an endless loop which is always waiting for an input from the user. Once it gets an input, it combines it with the nickname and sends it to the server. 

And lastly, we start two threads that run these two functions and the client's script is done, too.

### Running the Program

First, we run the server and the server starts listening. Then we run the client and set a nickname. Now we can start chatting with other clients.
