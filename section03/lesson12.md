## 12. Special Variables, Pseudocode, Command Substitution, if Statement, Conditionals.

---
> luser-demo02.sh
```sh
#!/bin/bash

# Display the UID and username of the user executing this script.
# Display if the user is the root user or not.

# Display the UID
echo "Your UID is ${UID}"

# Dispaly the username

# Dispaly if ther user is the root user or not.
   UID    Expands to the user ID of the current user, initialized at shell startup.  This variable is readonly.


```

```
[vagrant@localhost vagrant]$ ./luser-demo02.sh
Your UID is 1000
```

> if

```bash
if: if COMMANDS; then COMMANDS; [ elif COMMANDS; then COMMANDS; ]... [ else COMMANDS; ] fi
    Execute commands based on conditional.

    The `if COMMANDS' list is executed.  If its exit status is zero, then the
    `then COMMANDS' list is executed.  Otherwise, each `elif COMMANDS' list is
    executed in turn, and if its exit status is zero, the corresponding
    `then COMMANDS' list is executed and the if command completes.  Otherwise,
    the `else COMMANDS' list is executed, if present.  The exit status of the
    entire construct is the exit status of the last command executed, or zero
    if no condition tested true.

    Exit Status:
    Returns the status of the last command executed.
[vagrant@localhost vagrant]$

#### 0 is true.
```

```
[vagrant@localhost vagrant]$ type -a test
test is a shell builtin
test is /usr/bin/test
```

```
[root@localhost vagrant]# ./luser-demo02.sh
Your UID is 0
Your username is root
YOU ARE ROOT
```


help test | less


