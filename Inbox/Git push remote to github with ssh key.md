---
title : Git push remote to github with ssh key
date : 2021-07-24_Sat 10:14
aliases : [git, remote, github, ssh]
---
Source Type :: #📥/📄<br>
Source URL :: [git push 免帳號密碼 | ssh key](https://aben20807.blogspot.com/2018/03/1070302-git-push-ssh-key.html)<br>
Source Author :: [[@aben20807]]<br>
Note Type :: <br>
Topics :: [[]]<br>
Parent Link :: [[]]<br>

---
# Git push remote to github with ssh key

Generate ssh key
```bash
$ ssh-keygen -t rsa -C "your_email@example.com"                   #產生金鑰
Enter file in which to save the key (/home/harry90/.ssh/id_rsa):  #預設就好
Enter passphrase (empty for no passphrase):                       #不要輸入密碼
Enter same passphrase again:                                      #不要輸入密碼
```
<br>

Copy the ssh key to the github ssh key page
```bash
$ cat ~/.ssh/id_rsa.pub
ssh-rsa ~一連串金鑰~ ~"your_email@example.com"~
```
<br>

Run and test (==Important==)
```bash
$ ssh -T git@github.com
```