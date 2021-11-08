---
title : 📶Protocol layers, service model
date : 2021-11-07_Sun 13:25
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Computer Networks and the Internets]]<br>

---
# 📶Protocol layers, service model

## Internet protocol stack

| index |    name     |
|:-----:|:-----------:|
|   5   | application |
|   4   |  transport  |
|   3   |   network   |
|   2   |    link     |
|   1   |  physical   |

+ **application（應用層）**
	+ support network applications
		+ e.g. FTP, SMTP, HTTP
	+ DNS (domain name system)
		+ 把文字網址轉成數字 ip address
	+ 應用層的 packet 被稱為 message（訊息）
+ **transport（傳輸層）**
	+ 在應用程式端點間傳輸應用層 message
	+ TCP, UDP
	+ 傳輸層的 packet 被稱為 segment（區段）
+ **network（網路層）**
	+ routing of datagrams（資料報） from source to destination
	+ IP, routing protocols
	+ 網路層的 packet 被稱為 datagrams（資料報）
+ **link（連結層）**
	+ data transfer between neighboring network elements
	+ Ethernet, 802.111 (WiFi), PPP
	+ 連結層的 packet 被稱為 frame（框架）
+ **phisical（實體層）**

### ISO (International Organization for Standardlization)/OSI (Open System Interconnection) Model
| index |     name     |
|:-----:|:------------:|
|   7   | application  |
|   6   | presentation |
|   5   |   session    |
|   4   |  transport   |
|   3   |   network    |
|   2   |     link     |
|   1   |   physical   |

+ **presentation（表達層）**
	+ allow applications to interpret meaning of data
	+ e.g. encryption, compression, machine-specific conventions
+ **session（交談層）**
	+ synchronization（同步化）, checkpointing（檢查點）, recovery of data exchange

+ these services, *if needed*, must be implemented **in application**.


## Encapsulation（封裝）

![[Encapsulation.png]]

+ 只有第一層（實體層） -> repeater