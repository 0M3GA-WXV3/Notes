# BASH

### Links

https://cted.cybbh.io/tech-college/pns/public/pns/latest/guides/bash_sg.html

https://ss64.com/bash/

https://linuxhandbook.com/find-exec-command/

https://phoenixnap.com/kb/bash-printf

https://baeldung.com/linux/bash-single-vs-double-brackets

https://10.50.26.116/challenges

## Day 1

### Linux Commands

-  Symbols
```
&& = Logical and
! = Logical Not
| = Pipe
>> = Append
> = Redirect Output
```

```ls```    (-1, -lisa)    -    Show items

```rm```   (-f)   -    removes file

```rmdir``` (-r, -f)  -    removes directory

```mkdir``` (-p)   -    makes directory

```touch``` (-t)   -    makes file or can edit timestamp

```pwd```        -      show present working directory

```cat/more/less/tail/head```    -    show data in file

```find```    -    finds a file based on params
params:  
- (-name, -iname \*.txt, -maxdepth, -printf "%f %i\n")
- (-gid/uid, / -type d, -size | -/+1G)
- (-a/c/mtime 0, -a/c/mmin 60, -perm, 2>/dev/null)

```sudo``` (!!)    -    runs last command as root

```grep``` (-E, i, -n, v)   -    Prints alike matching pattern

```egrep```    -    Extended grep

```(p)kill``` (-9)    -    Kills specified program based on id or name

```killall```    -     Kills everything

```ps```(-elf)   -    shows process list

```cut``` (-d [Char to cut by] , -f1, -s)    -    cuts string outputs of file

### /etc/passwd formatting:

User ID  |  Group ID  |  /Home directory  |  Shell


<hr>

## Day 2

### Awk

```awk -F: '{print $NF}' fakepasswd```    -    NF prints last field
```awk -F: '($3 == 0) {print $1}' fakepasswd```    -    conditionals
```awk -F: 'BEGIN {OFS="@"} {print $1,$3}' fakepasswd ```    -    specifying fields
