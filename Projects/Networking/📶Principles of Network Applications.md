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
		+ FTP **server**: 20, 21
		+ SFTP (SSH) **server**: 22
		+ mail (SMTP) **server**: 25
		+ DNS **server**: 53
		+ HTML **server**: 80
		+ ...

## Transport Services Available to Applications
### App-layer protocols defines
+ **types of messages exchanged**
	+ e.g. request, response
+ message **syntax**
	+ what field（欄位） in messages & how fields are delineated（劃定）
+ message **semantics（語義）**
	+ meaning of informatin in fields
+ **rules** for when and how processes send & respond to messages

- open (public) protocols
	- defined in [[📶Introduction#Standards|RFCs]]
	- allows for interoperability（互動）
	- e.g. HTTP, SMTP, <u>3GPP - 3G, 4G, 5G</u>
- <u>proprietary protocols</u>（專有協議）
	- used in Company
	- e.g. Skype, Line...

### What transport service does an app need ?
data integrity, throughput, timing, security

#### data integrity（完整性） - reliable data transfer
+ some apps require 100% reliable data transfer
	+ e.g. file transfer, web transactions（交易）
	+ 此 apps 簡稱為 **data**
+ some apps can tolerate some loss
	+ e.g. audio, video
	+ 此 apps 為 **非data**

#### throughput（產出率、散出率）
+ some apps require minimum amount of throughput to be "effective"
	+ e.g. multimedia, streaming
	+ called **bandwidth-sensitive application**
+ some apps make use of whatever throughput they get
	+ called **elastic apps**

#### timing（時效性、時程）
+ some apps require low delay to be "effective"
	+ e.g. Internet telephony, interactive games

#### security
+ encryption, data integrity
+ ...

## Transport Services Provided by the Internet

|                  application | data loss     | throughput                                | time sensitive          |
| ----------------------------:|:------------- |:----------------------------------------- |:----------------------- |
|                file transfer | no loss       | elastic                                   | no                      |
|                       e-mail | no loss       | elastic                                   | no                      |
|                Web documents | no loss       | elastic                                   | no                      |
|        real-time audio/video | loss-tolerant | audio: 5Kbps-1Mbps<br>video: 10Kbps-5Mbps | yes, 100's milliseconds |
|           stored audio/video | loss-tolerant | audio: 5Kbps-1Mbps<br>video: 10Kbps-5Mbps | yes, few seconds        |
|            interactive games | loss-tolerant | few Kbps up                               | yes, 100's milliseconds |
| <u>text messaging</u> (data) | no loss       | elastic                                   | yes and no              |

### TCP service
+ **connection-oriented service（連線導向服務）**
	+ **setup（握手）** required between client and server processes
	+ 握手完後，稱為 TCP connection（TCP連線） 已存在於兩個行程的 sockets 之間
	+ TCP connection 為 full-duplex connection（全雙工連線）
+ **reliable transport** between sending and receiving process
+ **flow control:** sender won't overwhelm receiver
+ **congestion control:** throttle（節流、減速） sender when network overloaded
+ ==**does not provided:**== <u>timing</u>, <u>minimum throughput guarantee</u>, <u>security</u>

### UDP service
+ **unreliable data transfer** between sending and receiving process
	+ 用 UDP 的 app 可以自己（在應用層）做 reliable data transfer
+ ==**does not provided:**== <u>timing</u>, <u>throughput guarantee</u>, <u>security</u>, <u>reliability</u>, <u>flow control</u>, <u>congestion control</u>, <u>connection setup</u>...
+ ==**UDP is more flexible**==

> ### Securing TCP
> + TCP & UDP
> 	+ no encryption
> 	+ cleartext（明文） passwords sent into socket traverse Internet in cleartext
> + SSL (Secure Socket Layer)
> 	+ provides encrypted TCP connection
> 	+ data integrity (app layer)
> 	+ end-point authentication
> 	+ run at application layer
> 		+ apps use SSL libraries, that "talk" to TCP
> 	+ SSL socket API
> 		+ cleartext passwords sent into socket traverse Internet encrypted

##  Application-Layer Protocols
|                   application | application layer protocol                                              | underlying（底層） transport protocols |
| -----------------------------:|:----------------------------------------------------------------------- |:-------------------------------------- |
|                 e-mail (data) | SMTP \[RFC 2821\]                                                       | TCP                                    |
| remote terminal access (data) | Telnet \[RFC 854\]                                                      | TCP                                    |
|                    Web (data) | HTTP \[RFC 2616\]                                                       | TCP                                    |
|          file transfer (data) | FTP \[RFC 959\]                                                         | TCP                                    |
|  streaming multimedia (video) | HTTP (e.g. YouTube),<br>RTP (Real-time Transfer Protocols) \[RFC 1889\] | UDP                                    |
|    Internet telephony (audio) | SIP, RTP, proprietary (e.g. Skype)                                      | UDP                                    |

