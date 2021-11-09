---
title : 📶Principles of Network Applications
date : 2021-11-09_Tue 20:47
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Application Layer]]<br>

---
# 📶Principles of Network Applications
+ network-core devices do not function at the applcation layer, but instead function at the network layer and below.
+ The basic design above — namely, confining（限制） application software to the end systems — has facilitated（促進） the rapid development and deployment of a vast array of network applications.

## Application Architecetures
### client-server
| server                                                     | client                                      |
| ---------------------------------------------------------- | ------------------------------------------- |
|                                                            | communicate with server                     |
|                                                            | do not communicate directly with each other |
| always-on host (off -> breakdown)                          | may be intermittently（間歇地） connected   |
| permanent IP address                                       | may have dynamic IP address                 |
| **data center**（大型主機群） for<br>建立威力強大的虛擬伺服器 |                                             |

### peer-to-peer (P2P)
+ no always-on server -> pure p2p
+ arbitrary end systems directly communicate
+ peers request service from other peers, provide service in return to other peers
	+ **self-scalability（自我擴充性）:** new peers bring new service capacity, as well as new service demands
+ peers are intermittently（間歇地） connected and change IP address
	+ complex management
		+ 管理 -> extra server


## Processes communicating（行程通訊）
### Client and Server Processes
+ **process:** program running within a host
	+ within **same host**, two processes communicate using **inter-process communication** (defined by OS)
	+ process in different hosts communicate by exchanging messages

> - **client process:** process that **initiates communication**
> - **server process:** process that **waits to be contacted**
> 
> 
> ==different to **client-server** architecture==
> 
> * in P2P file sharing
> 	* **client process:** hosts that download files
> 	* **server process:** hosts that upload files

### The Interface Between the Process and the Computer Network - <u>Sockets</u>
+ process **sends/receives** messages to/from its ==sockets==
+ 類比於 door

### Addressing processes
+ to receive messages, process must have **identifier**
+ host device has unique IP address
	+ IPv4: 32-bit
	+ IPv6: 128-bit
+ **identifier** includes both **IP address** and **port numbers** associated with process (socket) on host.
	+ 常用的 port numbers:
		+ HTML **server**: 80
		+ m