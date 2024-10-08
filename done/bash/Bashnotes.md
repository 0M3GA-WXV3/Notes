# BASH

### Links

https://cted.cybbh.io/tech-college/pns/public/pns/latest/guides/bash_sg.html

https://ss64.com/bash/

https://linuxhandbook.com/find-exec-command/

https://phoenixnap.com/kb/bash-printf

https://baeldung.com/linux/bash-single-vs-double-brackets
079401
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

```cut``` (-d [Char to cut by] , -f1, -s)    -    cuts string outputs of file, add - at end of option to get everything following

```wc (-l)```     -    Word counter, -l counts lines

### /etc/passwd formatting:

User ID  |  Group ID  |  /Home directory  |  Shell


<hr>

## Day 2

### Awk & sort

```awk -F: '{print $NF}' fakepasswd```    -    NR prints first field, NF prints last field

```awk -F: '($3 == 0) {print $1}' fakepasswd```    -    conditionals

```awk -F: 'BEGIN {OFS="@"} {print $1,$3}' fakepasswd ```    -    specifying fields using output field separator

-  ```cat /etc/passwd | awk -F: '($3 >= 150){print $0}' fakepasswd``` 

-  ```cat /etc/passwd | awk -F: '($3 >= 150){print $1, $6, $3}' fakepasswd``` 

-  ```awk -F: '($7 == "/bin/bash"){print $1, $6, $3}' fakepasswd```

```awk -F: '($7 == "/usr/sbin/nologin"){print $1, $6, $3}' fakepasswd```    -    string comparison conditionals

-    n to sort numerically, nr for numerically reversed, -k for columns, -t for field separator, -u for unique
```awk -F: '{print $3}' fakepasswd | sort -n```    

```uniq```    -    must have sort before to work, works practically the same as "sort -u"

### Alias
set a command to do another command with
```
nano = 'vim'
```
### Sed

```sed -e 's/' (/g, /d)```    -    replaces characters/strings, /d delete the line, /g makes it global, not specifying only does first instance found

### Command substitution
``` ```

## Day 3

### if else
```
contents=$(cat simple.txt)
if [[ $contents == "tacos" ]]; then
  echo "are good on tuesdays"
elif [[ $contents == "costco is cool" ]]; then
  echo "and is cheap"
elif [[ $contents == "tacos" ]]; then
  echo "tasty but will make you fail ht/wt"
else
  echo "no tax at commisary"
fi
```
### Variable substitition
```
A="him"
echo This guy is literally $A
echo There is no girl that is a $A
```

### Compression
```tar (-czf)(-cvf)```    -    can compress a file
