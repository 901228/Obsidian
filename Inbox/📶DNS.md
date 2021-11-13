---
title : 📶DNS
date : 2021-11-13_Sat 11:04
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Application Layer]]<br>

---
# 📶DNS — The Internet’s Directory Service
+ DNS 可以指：
	+ distributed database
		+ 實做成 DNS server 階層架構的分散式資料庫。
	+ application-layer protocols
		+ 一種讓 hosts 可以查詢此一分散式資料庫應用層協定。

## DNS Services
+ **hostname** to **IP Address** translation
+ Hostname aliasing
	+ 名稱很複雜的 hostname 可以擁有多個 alias name
	+ canonical hostname（正規主機名稱）: 原本的 hostname
	+ Example: 
		+ **canonical hostname:** <small>relay1.west-coast.enterprise.com</small>
		+ **alias name:** <small>enterprise\.com, www\.enterprise\.com...</small>
+ Mail server aliasing
	+ mail server hostname 的 alias name
+ Load distribution（負載分配）
	+ 若網站擁有多台 server 可使用（多個 IP Address 共用一個 name），則當該網站流量高時，DNS 可以自動分配空閒的 server 給 client。

## Overview of How DNS Works
+ The problems with a centralized design
	+ **A single point of failure:** 如果 DNS server 掛了，整個網路也掛了。
	+ **Traffic volume:** 單一 server 需要處理所有（大量）的 DNS 查詢。
	+ **Distant centralized database:** 距離造成 delay。
	+ **Maintenance:** 資料量龐大，難以維護。
	+ 結論: <u>doesn't scale</u>（無法擴充）

### A Distributed, Hierarchical（階層式） Database
+ DNS classes
	1. root（根） DNS servers
	2. top-level domain (TDL)（高階網域） DNS servers
	3. authoritative（官方） DNS servers

```mermaid
graph TD;
	A[Root DNS Servers&nbsp&nbsp]-->B[com&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	B-->E[yahoo.com&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	B-->F[amazon.com&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	A-->C[org&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	C-->G[pbs.org&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	A-->D[edu&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	D-->H[poly.edu&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
	D-->I[umass.edu&nbsp&nbsp<br>DNS servers&nbsp&nbsp];
```

+ Example: client wants IP for www\.amazon\.com
	1. client queries root server to find com DNS server
	2. client queries .com DNS server to get amazon.com DNS server
	3. client queries amazon.com DNS server to get IP address for www\.amazon\.com

#### Root DNS Servers
+ 共 13 個 logical root name (\<A to M\>.root-servers.net)，分別由 13 個不同的組織管理。
+ 世界各地都有各個 root name server 的鏡像。
+ [root name server list](https://en.wikipedia.org/wiki/Root_name_server#Root_server_addresses)

#### TLD DNS Servers
+ 包含高階網域 com, org, sdu, gov...，與所有國家級的高階網域 uk, fs, ca, jp...，都有 TLD Servers。
	+ com 高階網域的 TLD Server 由 Verisign Global Registry Services 公司負責維護。
	+ edu 高階網域的 TLD Server 由 Educause 公司負責維護。

#### Authoritative DNS Servers
+ 所有機構，只要有 publicly accessible hosts on the Internet，就必須提供 publicly accessible DNS records, which mapping hostnames to IP Address。
+ DNS records can be stored in
	+ DNS Servers maintained by organization, university, company...
	+ 某家 service provider（服務供應商） 的 DNS Server 中（付費）。

#### Local DNS Name Servers
+ 不屬於 servers 階層架構中
+ each ISP has one
	+ alos called **default name server**
+ when host makes DNS query, query is sent to its local DNS server
	+ acts as proxy, forward query into hierarchy

### DNS name resolution example
host at cis.poly.edu wants IP address for gaia.cs.umass.edu

#### iterated query（實務上較常使用）
```mermaid
graph LR;
	B--1-->A[local DNS server&nbsp&nbsp<br>dns.poly.edu];
	A--8-->B[requesting host&nbsp&nbsp<br>cis.poly.edu];
	A--2-->C[root DNS server&nbsp&nbsp];
	C--3-->A;
	A--4-->D[TLD DNS server&nbsp&nbsp];
	D--5-->A;
	A--6-->E[authoritative DNS server&nbsp&nbsp<br>dns.cs.umass.edu];
	E--7-->A;
```
+ 從上游的 server 得到下游的 server name，在不斷迭代到找到目標 server 為止。
	+ "I don't know this name, but ask this server"

#### recursive query
```mermaid
graph TD;
	A--7-->B[local DNS server&nbsp&nbsp<br>dns.poly.edu];
	B--2-->A[root DNS server&nbsp&nbsp];
	A--3-->C[TLD DNS server&nbsp&nbsp];
	C--6-->A;
	B--8-->D[requesting host&nbsp&nbsp<br>cis.poly.edu];
	D--1-->B;
	C--4-->E[authoritative DNS server&nbsp&nbsp<br>dns.cs.umass.edu];
	E--5-->C;
```

### DNS Caching
+ 當 local DNS server 