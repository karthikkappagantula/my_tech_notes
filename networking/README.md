# Table of Contents
- [Table of Contents](#table-of-contents)
- [Network Protocal Fundamentals](#network-protocal-fundamentals)
  - [Terminology](#terminology)
  - [OSI Model](#osi-model)
[Top](#table-of-contents-)
* * *
# Network Protocal Fundamentals

* Formal standards and policies that define the way two or more devices communicate on a network.

* Network communication happens at different levels or layers(OSI Model or TCP/IP Model).
* Each layer of network communication is responsible for passing the information on to the next layer in the stack.
* Data transferred between layers is known as **Protocol Data Unit(PDU)**

## Terminology

* **LAN** - local area network - not publicly accessible by internet.
* **WAN** - wide area network - more broadly internet.
* **ISP** - internet server provider - company responsible for providing you access to internet.
* **NAT** - network address translation - allows requests from outside your local network to be mapped (or translated) to devices with in your local network.
* **Firewall** - piece of hardware or software that enforces what type of network traffic is and is not allowed. usually done by establishing rules for which ports should be externally accessible.
* **Router**  - allows trafer data back and forth between different networks.
* **Switch** - allows access between devices on a local network.
* **Network Interface** - allows you to connect to a public or private networks.
* **Port** - logically defined connection location. acts like destination endpoints for communication and transfer of data. programs that provide services to clients on a network run on a predefined ports between 0 and 65535(1 thru 1024 reserved for previliged services)
* **Packet** - basic unit of data transferred over a network. a package usually has a header that gives information about the packet (source, destination etc) and a body or payload containing actual data being sent.

## OSI Model
* Open Systems Interconnection Model - created by ISO.
* Breaks down network communication in to logical layers.
* Broken down to 7 layers - passes information from each layer to the next.
  * Layer 7 - Application
    * Implements several different protocols such as HTTP, FTP, SMTP.
    * These protocols allows applications to communication through networks and over internet.
  * Layer 6 - Presentation
    * Ensures that information is transferred in proper format for applications receiving it.
    * Compression and Encryption between applications that are communicating.
  * Layer 5 - Session
  * Layer 4 - Transport
  * Layer 3 - Network
  * Layer 2 - Data Link
  * Layer 1 - Pysical

