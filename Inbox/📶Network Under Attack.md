---
title : 📶Network Under Attack
date : 2021-11-07_Sun 15:20
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Computer Networks and the Internets]]<br>

---
# 📶Network Under Attack
+ security considerations in all layers.

## malware（惡意軟體）
+ **virus:** self-replicating infection by ==receiving/executing== object.
	+ 被動
	+ e.g. e-mail attachment
+ **worm:** self-replicating infection by ==passivelt receiving== object that gets itself executing.
	+ 主動

- **spyware malware** can *record keystrokes*, *web sites visited*, *upload info* to collection sire
- infected host can be enrolled in botnet（殭屍／傀儡網路）, used for spam.

## DoS (Denial of Service)
+ **Vulnerability attack**
+ **Connection flooding**
+ **Bandwidth flooding**
	+ **DDos (Distributed Dos):** ==<u>make resources (server, bandwidth) unavailable to legitimate traffic</u>== by ==<u>overwhelming resources with bogus traffic</u>==.
	+ 驅使殭屍網路進行攻擊。

## Sniff packets（竊聽封包）
+ 從 broadcast media (shared Ethernet, wireless) 被動接收 all packets, including passwords, private messages...

## IP spoofing（IP詐騙）
+ 用 fake（別人的、不存在的） ip 進行攻擊。