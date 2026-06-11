- **Explain the OSI Model (7 Layers)**
  - Application, Presentation, Session, Transport, Network, Data Link Layer, Physical Layer

- Difference between TCP and UDP.

- **How does a 3-way handshake work in TCP?**
  - A TCP 3 way handshake is a foundational process used to establish a reliable, connection-oriented session between a client and a server before any actual data is transmitted.

- **What is HTTP vs HTTPS?**
  - HTTP(Hypertext Transfer Protocol) : messages are plaintext, which means id send data on plan text.
  - HTTPS(Hypertext Transfer Protocol Secure) : Message are send in encryption format.

- **What is a Reverse Proxy?**
  - A reverse proxy is an intermediary server that sits in front of backend web services, intercepting client requests and forwarding them to the appropriate server

- **What is a Firewall**
  - A firewall is a network security device or software that monitors and filters incoming and outgoing network traffic.

- **Explain Load Balancing algorithms (Round Robin, Least Connection).**
  - Load balancer used to distribute incoming network traffic across multiple backend services. There are 2 type of Algorithms Round Robin, and Least Connections
  - _Round Robin_ : When client req arrive, the balancer passes them down the list one by one. one it reach last server. It loop back to the first server
  - _least Connection_ : The load balancer actively monitors and maintains a counter of ongoing. When a new request arrives, the load balancer evaluates these metrics and forward the traffic to the server with the absolute lowest number of active connections.
