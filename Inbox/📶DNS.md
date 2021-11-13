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
