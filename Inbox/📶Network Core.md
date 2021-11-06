---
title : 📶Network Core
date : 2021-11-04_Thu 13:41
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Computer Networks and the Internets]]<br>

---
# 📶Network Core
**Definition:** composed of packet switch and links, which is interconnecting the hosts (network edge)<br>

## Packet switching
**Definition:** Interchanging messages between hosts.<br>
&nbsp;&nbsp;&nbsp;&nbsp;**Packet:** smaller chunks of data from long messages.

+ Packets interchanged by <u>packet switch（封包交換器）</u>
	+ router
	+ link-layer switches

### Store and forward transmission
**Definition:** 交換器要先接收到完整的封包，才會繼續往下傳輸。<br>

```mermaid
graph LR;
	A[source]--R bps-----B((router));
	B--R bps-----C[destination];
```

+ Takes $\bf{\frac{L}{R}}$ seconds to transmit **L**-bit packet into link at **R** bps.
+ *store and forward:* entire packet must arrive at router before it can be transmitted on next link.
	+ resulting in **delay: $\bf{\frac{L}{R}}$**
	+ end-end delay: （視其他 delay 為 0）
		+ $(\ packet數 + link數 - 1\ ) \times \frac{L}{R}$