# 18. Positional Parameters, Arguments, for Loops, Special Parameters

---

> Man bash

> path
>
> 확인할것
> 
> echo ${PATH}
> 
> which head
> 


```
[vagrant@localhost vagrant]$ echo ${PATH}
/usr/local/bin:/usr/bin:/usr/local/sbin:/usr/sbin:/sbin:/usr/sbin:/home/vagrant/bin
[vagrant@localhost vagrant]$ which head
/usr/bin/head
```

# head
```
[root@localhost /]# which head
/usr/local/bin/head 
[root@localhost /]# which -a head
/usr/local/bin/head 
/bin/head
/usr/bin/head     
```

## man hash

```
which luser-demo06.sh

/usr/bin/which: no luser-demo06.sh in (/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin:/root/bin)
```

> 정리, /usr/local/bin과 ${0}의 관계

```
[root@localhost vagrant]# cp luser-demo06.sh /usr/local/bin/
[root@localhost vagrant]# which luser-demo06.sh 
/usr/local/bin/luser-demo06.sh
[root@localhost vagrant]# lu  
lua              luseradd         luser-demo06.sh
luac             luserdel         lusermod       
[root@localhost vagrant]# lu
lua              luseradd         luser-demo06.sh
luac             luserdel         lusermod       
[root@localhost vagrant]# lu
[root@localhost vagrant]# luser-demo06.sh
You executed this command: /usr/local/bin/luser-demo06.sh
```

## basename
> strip dir and suffix filename.
```
[vagrant@localhost vagrant]$ basename /vagrant/luser-demo06.sh 
```

```
luser-demo06.sh
```

>Example
```
[vagrant@localhost vagrant]$ cat /not/here
cat: /not/here: No such file or directory
[vagrant@localhost vagrant]$ basename /not/here
here
```

## dirname
> strip last component from file name
```
[vagrant@localhost vagrant]$ dirname /vagrant/luser-demo06.sh 
/vagrant
```
  

> EXAMPLE
```
[vagrant@localhost vagrant]$ dirname /this/is/not/here
/this/is/not
```

## param | ${#}, ${?}
```
[vagrant@localhost vagrant]$ ./luser-demo06.sh one
[1].. You executed this command: ./luser-demo06.sh
[2].. You used . as the path to the luser-demo06.sh script. 
[3]..YOU supplied 1 argument on the command line.

>>>

[vagrant@localhost vagrant]$ ./luser-demo06.sh a "b c" d
[1].. You executed this command: ./luser-demo06.sh
[2].. You used . as the path to the luser-demo06.sh script. 
[3]..YOU supplied 3 argument on the command line.

```

##  Type -a (command) 찌르기

```
[vagrant@localhost vagrant]$ type -a for
for is a shell keyword
```

---

## for
> for: for NAME [in WORDS ... ] ; do 
```
[vagrant@localhost vagrant]$ help for | head
for: for NAME [in WORDS ... ] ; do COMMANDS; done
    Execute commands for each member in a list.

    The `for' loop executes a sequence of commands for each member in a
    list of items.  If `in WORDS ...;' is not present, then `in "$@"' is
    assumed.  For each element in WORDS, NAME is set to that element, and
    the COMMANDS are executed.

    Exit Status:
    Returns the status of the last command executed.
```

```
[vagrant@localhost vagrant]$ for X in Frank Claire Dog
> do
>   echo "Hi ${X}."
> done
Hi Frank.
Hi Claire.
Hi Dog.
```
## for loop at sign...->[@]
```
for USER_NAME in "${@}"
do
  PASSWORD=$(date +%S%N | sha256sum | head -c48)
  echo "[${@}]... -> ${USER_NAME}: ${PASSWORD}"
done
```
> 결과 : 파라미터는 입력 안하면 출력없음.
```
[vagrant@localhost vagrant]$ ./luser-demo06.sh jason jake tom ted
[1].. You executed this command: ./luser-demo06.sh
[2].. You used . as the path to the luser-demo06.sh script. 
[3]..YOU supplied 4 argument on the command line.
[jason jake tom ted]... -> jason: 9c394ea826f8f6c5d73546f0f9490a47b7c17ca65798c21a
[jason jake tom ted]... -> jake: 5d4fca748f8ea5a9fef09e8e61cd82a27e04204d4c66d422
[jason jake tom ted]... -> tom: c25417289d4212873c5b476be18c0cca97b4c18750bf5725
[jason jake tom ted]... -> ted: 1fc69c77d669a68f13628686d31dca7389a0e3c2b77cdfbe
```
## # for loop Asterisk sign...->[*]

```
[vagrant@localhost vagrant]$ ./luser-demo06.sh jason jake tom ted
[1].. You executed this command: ./luser-demo06.sh
[2].. You used . as the path to the luser-demo06.sh script. 
[3]..YOU supplied 4 argument on the command line.
[jason jake tom ted]... -> jason jake tom ted: f6a4012b42ddec6d53ba3510ce63ee4b78246e0d8cfb3fee
```








# Appendix
## Special Parameters

```
   Special Parameters
       The shell treats several parameters specially.  These parameters may only be ref‐   
       erenced; assignment to them is not allowed.
       *      Expands  to the positional parameters, starting from one.  When the expan‐   
              sion occurs within double quotes, it expands to a  single  word  with  the   
              value  of  each parameter separated by the first character of the IFS spe‐   
              cial variable.  That is, "$*" is equivalent to "$1c$2c...", where c is the   
              first  character  of  the value of the IFS variable.  If IFS is unset, the   
              parameters are separated by spaces.  If IFS is null,  the  parameters  are   
              joined without intervening separators.
       @      Expands  to the positional parameters, starting from one.  When the expan‐   
              sion occurs within double quotes, each parameter  expands  to  a  separate   
              word.   That is, "$@" is equivalent to "$1" "$2" ...  If the double-quoted   
              expansion occurs within a word, the expansion of the  first  parameter  is   
              joined  with the beginning part of the original word, and the expansion of   
              the last parameter is joined with the last  part  of  the  original  word.   
              When  there  are  no  positional parameters, "$@" and $@ expand to nothing   
              (i.e., they are removed).
       #      Expands to the number of positional parameters in decimal.
       ?      Expands to the exit status of the most recently executed foreground  pipe‐   
              line.
       -      Expands  to  the current option flags as specified upon invocation, by the   
              set builtin command, or those set by the shell  itself  (such  as  the  -i   
              option).
       $      Expands  to  the process ID of the shell.  In a () subshell, it expands to   
              the process ID of the current shell, not the subshell.
       !      Expands to the process ID of the most recently executed background  (asyn‐   
              chronous) command.
       0      Expands  to  the  name of the shell or shell script.  This is set at shell   
              initialization.  If bash is invoked with a file of commands, $0 is set  to   
              the  name of that file.  If bash is started with the -c option, then $0 is   
              set to the first argument after the string  to  be  executed,  if  one  is   
              present.   Otherwise,  it  is set to the file name used to invoke bash, as   
              given by argument zero.
       _      At shell startup, set to the absolute pathname used to invoke the shell or   
              shell script being executed as passed in the environment or argument list.   
              Subsequently, expands to the last argument to the previous command,  after   
       !      Expands to the process ID of the most recently executed background  (asyn‐   
              chronous) command.
       0      Expands  to  the  name of the shell or shell script.  This is set at shell   
              initialization.  If bash is invoked with a file of commands, $0 is set  to   
              the  name of that file.  If bash is started with the -c option, then $0 is   
              set to the first argument after the string  to  be  executed,  if  one  is   
              present.   Otherwise,  it  is set to the file name used to invoke bash, as   
              given by argument zero.
       _      At shell startup, set to the absolute pathname used to invoke the shell or   
              shell script being executed as passed in the environment or argument list.   
              Subsequently, expands to the last argument to the previous command,  after   
              expansion.  Also set to the full pathname used to invoke each command exe‐   
              cuted and placed in the environment exported to that command.  When check‐   
              ing  mail,  this parameter holds the name of the mail file currently being   
              checked.
```