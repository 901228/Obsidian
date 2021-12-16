---
title : 📶transport-layer services
date : 2021-12-16_Thu 12:36
aliases : []
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[📶Computer Networking]]<br>
Parent Link :: [[📶Transport Layer]]<br>

---
# 📶transport-layer services
+ provide **logical communication（邏輯通訊）** between app processes running on different hosts
+ transport protocols run in end systems
	+ send side: breaks app messages into segments, passes to network layer
	+ recieve side: reassembles segments into messages, passes to app layer
+ more than one transport protocol available to apps
	+ Internet: TCP and UDP

## Transport layer vs Network layer
+ **network layer:** logical communication between **hosts**
+ **transport layer:** logical communication between **processes**

## Internet transport layer protocols
+ reliable, in-order delivery (TCP)
	+ congestion control
	+ flow control
	+ connection setup
+ unreliable, unordered delivery: UDP
	+ no-frills（多餘的） extension of “best-effort” IP
+ services not available:
	+ delay guarantees
	+ bandwidth guarantees
