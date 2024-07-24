### num 1

```
mkdir $HOME/{1123,1134,1145,1156}
```

### num 1.2

```
mkdir $HOME/1123 | touch $HOME/1123/{1,2,3,4,5,6~,7~,8~,9~}.txt
```

### num 1.3
```
find $HOME/1123/ -iname \*.txt
```
### num 1.4
```
find -iname \*.txt | grep -v '~'
```
### num 2
```
find $HOME/1123 -iname \*.txt -exec cp {} $HOME/CUT \;
rm $HOME/CUT/*~.txt \;
```
### num 3
```
find /var -empty -printf "%i %f\n" 2>/dev/null
```
### num 4
```
find / -inum 4026532575 -printf "%f\n"
```
### num 5
```
ls -l $HOME/CUT | grep "^-" | cut -d ' ' -f 9 | grep -v "names" > $HOME/CUT/names
```
### num 6
```
grep -P -o "(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})" StoryHiddenIPs | sort | uniq -c | sort -nr
```
### num 7
```
awk -F: '(($3 >= 4) && ($7 == "/bin/bash")){print $1}' passwd > $HOME/SED/names.txt
```
### num 8
```
dmesg | grep -P "CPU|BIOS" | grep -P -v -i "usable|reserved" | cut -d] -f2-
```
### num 9
```
a=$(openssl passwd -1 -salt bad4u Password1234)
awk -F: -v "awk_var=$a" 'BEGIN {OFS=":"} {$2=awk_var} {print $0}' $HOME/PASS/shadow.txt
```
### num 10
```
sed -e '/\/bin\/sh/d' -e '/\/bin\/false/d' $HOME/passwd >> $HOME/PASS/passwd.txt
```
