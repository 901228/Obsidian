---
title : 📶P2P
date : 2021-11-13_Sat 16:41
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Application Layer]]<br>

---
# 📶P2P (Peer-to-Peer)
+ Pure P2P architechture
	+ **no always on server**
	+ arbitrary end systens directly communicate
	+ peers are intermittently（間歇地） connected and change IP address
+ examples
	+ file distribution: BitTorrent
	+ Streaming: KanKan ?
	+ VoIP: Skype

## Scalability of P2P Architectures
```mermaid
graph LR;
	A[server]--u_s-->B((Internet));
	B--d_1-->C[client 1];
	C--u_1-->B;
	B--d_2-->D[client 2];
	D--u_2-->B;
	B--d_i-->E[client i];
	E--u_i-->B;
```
+ <u>distribution time</u>（傳布時間）: $N$ 個 peers 都收到一份檔案副本所花費的時間。
+ Predicate
	+ the upload rate of the server’s access link: $u_s$
	+ the upload rate of the ith peer’s access link: $u_i$
	+ the download rate of the ith peer’s access link: $d_i$
	+ the size of the file to be distributed: $F bits$
	+ the number of peers that want to obtain a copy of the file: $N$
+ Consequence
	+ For client-server
		+ server transmission
			+ time to send one copy: $F\ /\ u_s$
			+ time to send N copies: $NF\ /\ u_s$
		+ client
			+ $d_{min} = max\{d_1,\ d_2,...,\ d_N\}$
			+ min client download time: $F\ /\ d_{min}$
		+ distribution time: $$D_{cs} \ge max\bigg\{\frac{NF}{u_s}, \frac{F}{d_{min}}\bigg\}$$
			+ 只要 $N$ 夠大，$D_{cs}$ 就是 $NF\ /\ u_s$。
			+ 因此 $D_{cs}$ 可視為隨著 $N$ 的增加而線性增加。
	+ For P2P
		+ server transmission
			+ at least upload one copy: $F\ /\ u_s$
		+ client
			+ min client download time: $F\ /\ d_{min}$
		+ client
			+ $u_{total} = u_s + \sum^N_{i=1}u_i = u_s + u_1 + u_2 + ... + u_N$
			+ max upload rate: $NF\ /\ u_{total}$
		+ distribution time: $$D_{P2P} \ge max\bigg\{\frac{F}{u_s}, \frac{F}{d_{min}}, \frac{NF}{u_{total}}\bigg\}$$
			+ 只要 $N$ 夠大，$D_{P2P}$ 就是 $NF\ /\ u_{total}$。
			+ 因此 $D_{P2P}$ 可視為隨著 $N$ 的增加而非線性增加。
![[client-server versus P2P.png]]

## BitTorrent
+ **torrent（奔流）:** 所有參與檔案傳輸的 peers
+ file divided into 256KB chunks（一般來說）
+ **tracker（追蹤者）:** 基礎節點，記錄所有在 torrent 中的 peers。

- 當 Alice 加入 torrent 中時
	1. 向 tracker 登錄自己
	2. 向 tracker （隨機）取得一份 peers list
	3. 嘗試向 list 上的所有 peers 建立 TCP connections
	4. 若成功建立連線，該節點稱為 **neighbors**
	5. ==neighbor 數量會隨著時間（節點增加、離開）而改變。==
- 任一時刻，每個 peers 都持有部份的 chunks，不同 peers 持有不同的 chunks
- 週期性的，Alice 