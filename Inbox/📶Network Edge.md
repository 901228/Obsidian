---
title : 📶network edge
date : 2021-10-30_Sat 20:16
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Computer Networking]]<br>

---
# 📶network edge

+ network edge (host): clients and servers
+ network core:
	+ interconnected ==routers==
	+ network of networks

## Access network
### Home Access	
#### Digital Subscriber Line (DSL)
![[DSL.png]]

+ use *existing* telephone line to exchange data from DSLAM (DSL access multiplexer（匯集器、多工器）) in CO (central office)
	+ data upstream use bandwidth between 50kHz ～ 1MHz
	+ data downstream use bandwidth between 4kHz ～ 50kHz
	+ voice (telephone) use bandwidth between 0 ～ 4kHz
+ asymmetric（不對稱性）:
	+ 15Mbps upstream transmission rate
	+ 55Mbps downstream transmission rate
+ 只適用於距離 CO 距離較短的情況。

#### Cable Internet access
+ network of cable, fiber attaches homes to ISP router
	+ home share access network to cable headend
	+ use *existing* television cable to exchange data from CMTS (Cable modem termination system) in CO (central office)

+ HFC (fybird fiber coax) （混合<u>光纖</u><span style="font-size: 0.3em;"> </span><u>同軸網路</u>）
	+ 先用<u>光纖</u>送到住宅區附近的交換站，再用<u>同軸電纜</u>送到各個家庭中。
	+ asymmetric: up to 42.8Mbps downstream rate, 30.7Mbps updtream rate.

+ FTTH (fiber to the home) （光纖到府）: 全都是光纖
	+ direct fiber（導向光纖）: 每戶家庭都有一條光纖直接接到 CO
	+ 較常見: 到住家附近前都還是一條線路
		+ AON (active optical network)
		+ PON (passive optical network)

### Access in the Enterprise (and the Home)
#### Enterprise access networks (Ethernet)
![[Ethernet.png]]
+ Typically used in companies, universities, etc.
+ 10Mbps, 100Mbps, 1Gbps, 10Gbps transmission rates.
+ end systems typically connect into Ethernet switch

#### Wireless access networks
+ access point: shared wireless access network connects end system to router

##### wireless LANs (Local Area Network):
+ 距離: 數十<u>公尺</u>內。
+ 802.11 (WiFi): > 100Mbps transmission rate

##### wide-area wireless access (WAN (Wide Area Network))
+ 距離: 基地台為中心方圓數十<u>公里</u>内。
+ between 1 and 10Mbps
+ 3G, 4G LTE

## Phsical media
+ guided media: wire, fiber...
+ unguided media: WiFi, satellite...

### <u>Twisted-Pair</u> Copper Wire
+ Used in the networks in buildings (LAN)
+ 10Mbps ～ 1Gbps transmission rate

### Coaxial（同軸（平行）） Cable
### Fiber Optics
+ 传输速率高

### Terrestrial Radio Channels
