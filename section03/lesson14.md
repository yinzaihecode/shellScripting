## 14 Reading Standard Input, Creating Accounts, Username Conventions, More Quoting.

---

```sh
[vagrant@localhost ~]$ cd /vagrant/
[vagrant@localhost vagrant]$
[vagrant@localhost vagrant]$ type -a read
read is a shell builtin
read is /usr/bin/read

help read | less
read -p 'Type something: ' THING
```

---

```
[vagrant@localhost vagrant]$ read -p 'Type something: ' THING
Type something: something
[vagrant@localhost vagrant]$ echo ${THING}
something
[vagrant@localhost vagrant]$
```



```sh
input[3]

standard input
standard output
standard error


```


# useradd
---

NAME
       useradd - create a new user or update default new user information

SYNOPSIS
       useradd [options] LOGIN

       useradd -D

       useradd -D [options]
       