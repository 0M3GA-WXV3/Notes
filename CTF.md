### num 1
Brace expansion is a mechanism by which arbitrary strings may be generated, for commands that will take multiple arguements. For the below examples, the first example is equivalent to the second command.
```
mkdir $HOME/{1123,1134,1145,1156}
```

### num 1.2
Use Brace-Expansion to create the following files within the $HOME/1123 directory. You may need to create the $HOME/1123 directory. Make the following files, but utilze Brace Expansion to make all nine files with one touch command.
```
mkdir $HOME/1123 | touch $HOME/1123/{1,2,3,4,5,6~,7~,8~,9~}.txt
```

### num 1.3
Using the find command, list all files in $HOME/1123 that end in .txt.
```
find $HOME/1123/ -iname \*.txt
```
### num 1.4
List all files in $HOME/1123 that end in .txt. Omit the files containing a tilde (~) character.
```
find -iname \*.txt | grep -v '~'
```
### num 2
Copy all files in the $HOME/1123 directory, that end in ".txt", and omit files containing a tilde "~" character, to directory $HOME/CUT.
```
find $HOME/1123 -iname \*.txt -exec cp {} $HOME/CUT \;
rm $HOME/CUT/*~.txt \;
```
### num 3
Using ONLY the find command, find all empty files/directories in directory /var and print out ONLY the filename (not absolute path), and the inode number, separated by newlines.
```
find /var -empty -printf "%i %f\n" 2>/dev/null
```
### num 4
Using ONLY the find command, find all files on the system with inode 4026532575 and print only the filename to the screen, not the absolute path to the file, separating each filename with a newline. Ensure unneeded output is not visible.
```
find / -inum 4026532575 -printf "%f\n"
```
### num 5
Using only the ls -l and cut Commands, write a BASH script that shows all filenames with extensions ie: 1.txt, etc., but no directories, in $HOME/CUT. Write those to a text file called names in $HOME/CUT directory. Omit the names filename from your output.
```
ls -l $HOME/CUT | grep "^-" | cut -d ' ' -f 9 | grep -v "names" > $HOME/CUT/names
```
### num 6
Write a basic bash script that greps ONLY the IP addresses in the text file provided (named StoryHiddenIPs in the current directory); sort them uniquely by number of times they appear.
```
grep -P -o "(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})" StoryHiddenIPs | sort | uniq -c | sort -nr
```
### num 7
Using ONLY the awk command, write a BASH one-liner script that extracts ONLY the names of all the system and user accounts that are not UIDs 0-3
```
awk -F: '(($3 >= 4) && ($7 == "/bin/bash")){print $1}' passwd > $HOME/SED/names.txt
```
### num 8
Find all dmesg kernel messages that contain CPU or BIOS (uppercase) in the string, but not usable or reserved (case-insensitive) Print only the msg itself, omitting the bracketed numerical expressions ie: [1.132775]
```
dmesg | grep -P "CPU|BIOS" | grep -P -v -i "usable|reserved" | cut -d] -f2-
```
### num 9
Write a Bash script using "Command Substitution" to replace all passwords, using openssl, from the file $HOME/PASS/shadow.txt with the MD5 encrypted password: Password1234, with salt: bad4u
```
a=$(openssl passwd -1 -salt bad4u Password1234)
awk -F: -v "awk_var=$a" 'BEGIN {OFS=":"} {$2=awk_var} {print $0}' $HOME/PASS/shadow.txt
```
### num 10
Using ONLY sed, write all lines from $HOME/passwd into $HOME/PASS/passwd.txt that do not end with either /bin/sh or /bin/false.
```
sed -e '/\/bin\/sh/d' -e '/\/bin\/false/d' $HOME/passwd >> $HOME/PASS/passwd.txt
```
### num 11
Using find, find all files under the $HOME directory with a .bin extension ONLY.
```
find $HOME -name \*.bin -printf "%h\n" | sort -u
```

### num 12

```
```

### num 13

```
find /bin /sbin /usr/bin /usr/sbin -type f -executable -print | sort | tail -10 | echo "06ee74ac18ceec20497e38b5c6c39e5c"
```
