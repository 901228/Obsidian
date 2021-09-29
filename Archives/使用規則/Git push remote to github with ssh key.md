---
title : Git push remote to github with ssh key
date : 2021-07-24_Sat 10:14
aliases : [git, remote, github, ssh]
---
Source Type :: #📥/📄<br>
Source URL :: [git push 免帳號密碼 | ssh key](https://aben20807.blogspot.com/2018/03/1070302-git-push-ssh-key.html)<br>
Source Author :: [[@Github]]<br>
Note Type :: #⚙️ <br>
Topics :: [[使用規則]]<br>
Parent Link :: [[使用規則]]<br>

---
# Git push remote to github with ssh key

## Generate a new SSH key
```shell
$ ssh-keygen -t ed25519 -C "901228@gmail.com"
> Generating public/private ed25519 key pair.
When you\'re prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

> Enter a file in which to save the key (/home/you/.ssh/id_ed25519): [Press enter]

> Enter passphrase(password) (empty for no passphrase): [Type a passphrase]
> Enter same passphrase again: [Type passphrase again]
```
<br>

##  Adding your SSH key to the ssh-agent
```shell
$ eval "$(ssh-agent -s)"
> Agent pid 59566
```

```shell
$ ssh-add ~/.ssh/id_ed25519
$ sudo ssh-add /home/harry90/.ssh/id_ed25519
```

> ```shell
> 如果出現
> > Could not open a connection to your authentication agent.
> 
> 進去 ssh bash 再繼續
> $ ( sudo ) ssh-agent bash
> $ ssh-add /home/harry90/.ssh/id_ed25519
> ```

<br>

## Copy the SSH key to the Github SSH key page
```shell
$ xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```
<br>

## Change the remote repository url
```shell
$ git config remote.origin.url <Github Repository SSH URL>
```
<br>

## (==Important==) Run and test (ssh)
```shell
$ ssh -T git@github.com
The authenticity of host 'github.com (52.192.72.89)' can\'t be established.
RSA key fingerprint is SHA256: ~SHA256 Key~.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,52.192.72.89' (RSA) to the list of known hosts.
Hi 901228! You\'ve successfully authenticated, but GitHub does not provide shell access.
```
<br>

## (==Important==) Personal Token (replace above)

> ==generate personal token on github==
> <p style="font-size:12">(Settings -> Developer Settings -> Personal Access Token -> Generate New Token -> Fillup the form -> click Generate token -> Copy the generated Token)</p>

```shell
$ git remote set-url origin https://<token>@github.com/<username>/<repo>
```
<br>

## (==Important==) Run and test (git push)

```shell
$ git push
Username for 'https://github.com': 901228
Password for 'https://901228@github.com':    #password
...
...
```