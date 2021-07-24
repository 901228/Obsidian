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
```shell
$ ssh-keygen -t rsa -C "your_email@example.com"
```
<br>

```shell
Enter passphrase:
```


Copy the ssh key
```shell
$ cat ~/.ssh/id_rsa.pub
```

```shell
```