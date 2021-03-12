## 11. Getting Started with Shell Scripting: Naming, Permissions, Variables, Builtins.
---

C:\Users\jay\shellclass>mkdir localusers

C:\Users\jay\shellclass>cd localusers

C:\Users\jay\shellclass\localusers>
```
vagrant init jasonc/centos7
vagrant up 
vagrant ssh

 

```

`default: /vagrant => C:/Users/jay/shellclass/localusers`

---



```
C:\Users\jay\shellclass\localusers>
C:\Users\jay\shellclass\localusers>vagrant ssh
[vagrant@localhost ~]$
[vagrant@localhost ~]$ cd /vagrant
[vagrant@localhost vagrant]$ ls -l
total 4
```
`-rwxrwxrwx 1 vagrant vagrant 3090 Mar  6 20:47 Vagrantfile`


## 용어 설명

* '#' = sharp
* '!' = Bang
* '#!' = Shebang (쉬뱅ㅋㅋ)
* . = period
* / = slash

---

```
#!/bin/bash
#!/usr/bin/python
#!/bin/ruby

```

## 권한 설정

`-rwxrwxrwx   1 vagrant vagrant  101 Mar  6 21:29 luser-demo01.sh`

* r : read  : 4
* w : write  : 2
* x : excuteable. : 1
* 7 = 4+2+1 : r+w+x 
* 5 = 4 + 1 : r+x


---

* represents
  * [1] the owner of the file
  * [2] groups
  * [3] everyone else on the system

`[vagrant@localhost vagrant]$ ./luser-demo01.sh` \
Hello


```
[vagrant@localhost vagrant]$ type echo
echo is a shell builtin

[vagrant@localhost vagrant]$ type -a echo
echo is a shell builtin
echo is /usr/bin/echo

[vagrant@localhost vagrant]$ echo 'Hello'
Hello
```

```
[vagrant@localhost vagrant]$ type -a uptime
uptime is /usr/bin/uptime
```





