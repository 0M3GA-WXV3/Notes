# Networking Mod
  ---
# Day 1
![image](https://github.com/user-attachments/assets/4e19d0a5-4a57-4a2a-95ec-431ca9a21c4c)
  ## Links
  *  http://networking-ctfd-1.server.vta:8000/
  *  https://miro.com/app/board/o9J_klSqCSY=/
  *  https://explainshell.com
  *  https://ss64.com

  ## Logging into blue internet host714432
    ```
    ssh student@10.50.38.83 -X
    password
    ```

## Floating IPs
  An IP which will allow access to internal networks, will redirect you to a new internal station to use and will show the internal private IP once accessed. In essence, a redirector.
## OSI Model
![image](https://github.com/user-attachments/assets/abaac8a7-609d-45ed-bad8-d45524e0556c)

## Internet Standards Organizations
  *   IETF - In charge of RFCs index
  *   IANA - In charge of IP addresses, root resolver that can restrict and provides assignments of domains
  *   IEEE - In charge of hardware standards, electrical engineers that manage the devices

## Binary
  Base2, uses only 0 and 1
  
  ```bit, nibble, byte, half-word, word```
## Decimal
  Base10, 0-10
  
  ```1,2,3,4,5,6,7,8,9,10```
## Hex
  Base16, 0-9, A-F
  
  ```1,2,3,4,5,6,7,8,9,10,A,B,C,D,E,F```
## Base64
  64 Symbols, A-Z, a-z, 0-9, +, /
  
  ```=``` is used to represent a null value

## Networking Topologies
  *  Bus  -  All connected to same terminator line
  *  Star  -  All connected to one device, can communicate through it
  *  Ring  -  All connected one to the next in a circle
  *  Mesh  -  Certain device connected to other ones, if any one goes down, network is still up
  *  Wireless  -  Wireless receiver/router, will communicate through other devices on same interface
  *  Hierarchial  -  Allows segmenting network so only certain device in a certain layer can access certain devices/networks
## Networking Devices
  *  Hubs
  *  Repeaters
  *  Switches
  *  Routers
## Ethernet timing
  *  10Mbps = 100ns
  *  100 Mbps = 10ns
  *  1Gbps = 1ns
  *  10Gbps = .1ns
  *  100Gbps = .01ns
## Lan Technologies
  *  Ethernet - 802.3(x)
  *  Wireless 802.11(x)
  *  Token Ring 802.5
## Data Link Sublayers
  *  MAC  -  Medium Access Control Address is a hardware identifying address to send/receive networking data
  *  LLC  -  Logical Link Control maintains the link to the receiving address

## How switches affect network traffic & visibility
  *   Builds a CAM Table (MAC addresses)
      Learns by reading Source MAC
  *   Forwarding Frames
      Decision based on Destination

## Switches Modes
      *    Cut-through - (aka, Fast Forward)
      *    Fragment-Free - 
      *    Store-and-Forward - Accepts, analyzes and forwards

## Exploit
      *    CAM Tables Overflow Attack
            Send Frames w/ bogus source MAC to switch
      *    Causes switch to fill the table with corrupted addresses and will be unable to learn valid MAC addresses
## Mac Addresses
48-bit | 6-byte | 12 Hex  

Windows: XX-XX-XX-XX-XX-XX

Linux: XX:XX:XX:XX:XX:XX

Cisco: XXXX.XXXX.XXXX

OUI  -  First 24-bits assigned by IANA

Vendor Assigned  -  Last 24-bits assigned by vendor

  *  Types:
        Unicast - One talking to One
           8th bit is off
        Multicast - One talking to many
           8th bit is on
        Broadcast - One talking to all
           All bits are on

## Mac Spoofing
*  Could not be changed at first, now can be changed w/ software
*  Used to be called hardware,firmware,burned-in

## Ethernet Header & Frame
<br>![image](https://github.com/user-attachments/assets/e48801b1-b84f-4161-922c-31df95bda921)
  *  Frame 2 Header
<br>![image](https://github.com/user-attachments/assets/e49eb709-229f-43fe-bb9b-3ea64827b1bd)
  *  Traffic Type Header
<br>![image](https://github.com/user-attachments/assets/218d5748-8bdd-47b0-9c93-66b6a1773034)

## VLAN
  *  Default = VLAN 1
  *  Trunk Lines = Method to transfer data securely from one device on a VLAN to another without overlapping with other VLANs
  *  Data = User Traffic
  *  Voice = VOIP
  *  Management = Switch & Router management
  *  Native = Untagged switch and router traffic

## 802.1Q Header
![image](https://github.com/user-attachments/assets/2493030a-7c4f-4ee2-a507-c60750a5e07e)
## 802.1AD Header
![image](https://github.com/user-attachments/assets/96dc3383-8473-41f2-9f52-19f796a901e0)

## VLAN Hopping Attack
  *  Switch Spoofing (DTP)
  *  Single Tagging
  *  Double Tagging (Using Native VLAN)
  *  SCAPY

## ARP (Address Resolution Protocol)
![image](https://github.com/user-attachments/assets/7f3ecaae-9924-423c-b568-882bfc0ae570)

### ARP Types
  *  ARP (OP 1 & 2)
  *  RARP (OP 3 & 4)
  *  Proxy ARP (OP 2)
  *  Gratuitous ARP (OP 2)
### ARP Cache
  *  All resolved MAC to IP resolutions
  *  If MAC isn't in Cache then ARP is used
  *  Dynamic entries last from 2-20 Minutes
  *  Default Gateway is present at minimum
  *  Can be easily duped by attackers
### MITM w/ ARP
  *  Poison ARP Cache w/ Gratuitus ARP & Proxy Arp using SCAPY

## VTP & Vulnerabilities
  *  VTP (VLAN Trunking Protocol)
      Dynamically add,remove, or modify VLANs
      It is Cisco proprietary, and has 3 modes
      Server, Client, & Transparent
  *  Vulnerability
      Can cause switch to dump all VLAN information
      Causes a DoS as the switch will not support configured VLANs
## DTP (Dynamic Trunking Protocol)
  *  Cisco Proprietary w/ 2 Modes: Dynamic-Auto and Dynamic-Desirable
  *  DTP Vulnerability
      On by default, can send crafted messages to form a VLAN Trunk Link,
      will disable DTP negotiations & manually assign as Access or Trunk
## CDP, FDP, and LLDP
  *  Cisco Discovery Protocol
  *  Foundry Discovery Protocol
  *  Link Layer Discovery Protocol
### Vulnerability
  *  Leaks valuable information
  *  Clear text
  *  Enabled by default
  *  Disable it Globally or Per Interface
  *  May require for VOIP
## STP (Spanning Tree Protocol)
  *  Root Decision process
      1. Elect Root Bridge
      2. Identify root ports on non-root bridge
      3. Identify Designated port for each assignment
      4. Set alternate ports for blocing state
  *  802.1D STP
      Per VLAN STP
## Port Security
  Security Modes
  *  Shutdown (default)  -  Will Disable the port entirely
  *  Protect  -  Will drop packets it doesn't believe should be there
  *  Restrict  -  Will create a log of the MAC address accessing the port
  Can help
     Restrict unauthorized access, limit MAC addresses learned on port, and prevent CAM Table overflow attacks
  Vulnerabilities
  *  Dependant on MAC address
  *  MAC Spoofing
  Mitigations
  *  Shutdown unused ports
  *  Enable port security
  *  IP Source Guard
  *  Manually assign STP root
  *  BPDU Guard
  *  DHCP Snooping
  Attack Mitigations
  *  802.1X
  *  Dynamic ARP Inspection
  *  Static CAM Entries
  *  Statis ARP entries
  *  Disable DRP negotitations
  *  Manually assign Access & Trunk ports

## Network Layer
  *  Addressing Scheme for Network (Logical Addressing)
  *  IP Fragmentation & Reassembly
  *  Error Handling & Diagnostics
  *  Encapsulation
  *  Routing
## IP Versions
IPv4 (ARPANET 1982)
  *  Classful subnetting

      ~  Class A (0 - 127)
     
      ~  Class B (128 - 191)
     
      ~  Class C (1292 - 223)
     
      ~  Class D (224 - 239) - Multicasting
     
      ~  Class E (240 - 255) - Not Used
     
  *  Classless subnetting (CIDR)
  *  NAT
IPv6 (Standardized in 2017)

## Subnetting
  *  IP Addresses:
      Network Portion
      Host Portion
  *  Practice of borrowing host bits and using them as subnet bits
## Address Types
  *  Unicast
      Classes A - C
  *  Mutlicast
      Class D
  *  Broadcast
      Broadcasts to any IP on local network
## Address Scopes
  *  Public
  *  Private
  *  Loopback (127.0.0.0/8)
  *  Link-Local (APIPA)
  *  Multicast (Class D)
## Fragmentation
  *  Routers breaking up packets from higher to lower MTU networks 
  *  MF flag is on from 1st packet until it reaches the last one
  *  Offset = (MTU - (IHL * 4)) / 8
## IPv6 Fragmentation
  *  Header does not allow fragmentation by default
  *  Source can use an extension header to allow it
## Vulnerability
  *  Can use fragmentation overlaps to avoid firewall detection
  *  Attack depends on how OS deals with overlap
## TTL to get OS
  *  Linux = 64
  *  Windows = 128
  *  Cisco = 255
## IPv4 Auto Config
  *  APIPA

      169.254.0.0/16
     
      RFC 3927
  *  DHCP

     DORA Process
     
      RFC 1531
     
  *  Vulnerabilities
    
     Evil Twin
     
     Rogue DHCP
     
     DHCP Starvation
     
## ICMPv4 Types & Codes
![image](https://github.com/user-attachments/assets/e0576c72-5fb9-44e3-a83e-fa3c69570a85)

## IPv4 OS Indicators
  *  Linux:
      Default Size = 64 Bytes
      Payload = !\"#\$%&\'()*+,-./0123456789
  *  Windows:
      Default Size = 40 Bytes
      Payload = abcdefghijklmnopqrstuvwxyz
## IPv4 Traceroute
  *  Windows uses ICMP
  *  Linux uses UDP
  *  also TCP as an option
## ICMPv4 Attacks
  *  Firewalking
  *  Oversized ICMP messages
  *  ICMP Redirects
  *  SMURF Attack
  *  Map network w/ IP unreachables
  *  ICMP Covert Channels
## IPv6
  *  Much bigger packet header
  *  Can be shorten only once, separates by colons and can remove all 0s
## IPv6 Address Scopes
  *  Global Unicast Adresses
  *  Unique Local
  *  Loopback
  *  Link-Local
  *  Multicast
## IPv6 Vulnerabilities
  *   MITM
  *   Enumerate OS
  *   Rogue DHCP
  *   Evil Twin
  *   DHCP Starvation

## NDP
  *  Router Solicitation
  *  Router Advertisement
  *  Neighbor Solicitation
  *  Neighbor Advertisement
  *  Redirect

## Metrics
  *  RIP - Hops
  *  EIGRP - Bandwith, Delay, Load Reliability
  *  OSPF - Cost
  *  BGP - Policy

## Classful vs Classless
![image](https://github.com/user-attachments/assets/f7d8bfd7-b9f9-4b3d-9a79-1a0f79f12657)

## Routed (ie. SSH, Telnet, RDP) vs Routing Protocols (ie. IP, IPX, AppleTalk)
![image](https://github.com/user-attachments/assets/a3976243-1577-488f-ab58-84a0c3f977d5)

## IGP (Internal Gateway Protocol) & EGP (External Gateway Protocol)
![image](https://github.com/user-attachments/assets/b73a338a-b2fb-4801-968a-e190b0b3f19f)

## Autonomous Systems
  *   Assigned by IANA
  *   Numbers assigned to identify different organizations and to see what protocol they will use (ie. EIGRP, RIP, OSPF)
  *   Autonomous Systems can check packet using their set protocol to ensure the Number matches with theirs, will ignore it if not for them

## Static Routes - Pros/Cons
![image](https://github.com/user-attachments/assets/41e3a6eb-8976-4186-95c2-98f95166db82)

## Dynamic Routes - Pros/Cons
![image](https://github.com/user-attachments/assets/cb1fa6a8-7325-4839-805a-d4a58c5924da)

## First Hop Redundancy
![image](https://github.com/user-attachments/assets/7ec5832a-3dfb-4772-96b7-23b186192e53)

  *   FHRP Attack
        Intercept FHRP message exchange
        Inject manipulated messages
        MITM by becoming active forwarder

## Port Ranges
  *  0 - 1023 | Well Known System Ports
  *  1024 - 49151 | Registered User Ports
  *  49152 - 65535 | Dynamic Private Port (aka. Ephemeral High Port)

## VPN
  Types
  *  RAT (Client - Site)
  *  Site - Site

## Layer 6 of OSI
   Anything translation based
       *  Translation
       *  Formating
       *  Encoding
       *  Encryption
       *  Compression
## SSH Key Files
  *  Known Hosts
      ``` ~/.ssh/known_hosts ```
     
  *  Config Files

      ```/etc/ssh/ssh_config ```
     
      ```/etc/ssh/sshd_config ```
## SSH Keygen
      ssh-keygen -t rsa -b 4096 -C "User"

## HTTP Vulnerabilities
  *  Flooding
  *  Amplification
  *  Low & Slow
  *  Drive-by Downloads
  *  BeEF Framework

# Day 2

## Packet Collection
  *  Use Wireshark, TShark, TCPDump, etc
  *  OS Fingerprinting in P0F, -r to read pcap and -i to read interface
      Signitute DB: less /etc/p0f/p0f.fp
  *  BPFs suck ass

# Day 3

## Sockets
  *  Stream Sockets - Connection oriented and sequenced; methods for connection establishment and tear-down. Used with TCP, SCTP, and Bluetooth.
  *  Datagram Sockets - Connectionless; designed for quickly sending and receiving data. Used with UDP.
  *  RAW Sockets - Let's us create packets, how the internet works and programs talk to each other

## User Space & Kernel Space sockets
  *  Userspace Sockets

      ^  Stream Sockets

      ^  Datagram Sockets

  *  Kernel Space Sockets

      ^  RAW Sockets

  *  User Space Sockets - The most common sockets that do not require elevated privileges to perform actions on behalf of user applications.

  *  Kernel Space Sockets - Attempts to access hardware directly on behalf of a user application to either prevent encapsulation/decapsulation or to create packets from scratch, which requires elevated privileges.

  *  Userspace Applications
       Using tcpdump or wireshark to read a file
     
       Using nmap with no switches

       Using netcat to connect to a listener

       Using netcat to create a listener above the well known port range (1024+)

       Using /dev/tcp or /dev/udp to transmit data
  *  Kernelspace Applications

      Using tcpdump or wireshark to capture packets on the wire

      Using nmap for OS identification or to set specific flags when scanning

      Using netcat to create a listener in the well known port range (0 - 1023)

      Using Scapy to craft or modify a packet for transmission

      Using Python to craft or modify RAW Sockets for transmission

      Network devices using routing protocols such as OSPF

      Any Traffic without Transport Header (ICMP)Day 1

  *  Python

      ```import {module}```  -  Will import a module to python to use its libraries
     
      ```from {module} import *```  -  Will allow calling of functions from module

  *  Socket.socket

          ```import socket
          s = socket.socket(socket.FAMILY, socket.TYPE, socket.PROTOCOL)```

     Inside the socket.socket. function, you have these arguments, in order:

     ```socket.socket( *family*, *type*, *proto* )```
     
        family: ```AF_INET*, AF_INET6, AF_UNIX```

        type: ```SOCK_STREAM*, SOCK_DGRAM, SOCK_RAW```

        proto: ```0*, IPPROTO_TCP, IPPROTO_UDP, IPPROTO_IP, IPPROTO_ICMP, IPPROTO_RAW```

  *  Python Network Programming

      ![image](https://github.com/user-attachments/assets/ac19f933-3dd9-47c5-b30e-7987dcb787ef)

      By default, it will decode into UTF-8

  ##Encoding vs Decryption
    
  Encoding is the process of taking bits and converting them to a set cipher
     
   Decoding is reverse process to get the encoded data
     
  Encryption scrambles data to make it completely unlegible and "near" impossible to reverse without a key

   Examples.
    
  Encode Text to Hex
     
                 echo "Message" | xxd
     
  Encode to Hex
     
                 xxd file.txt file-encoded.txt
     
  Decode file From Hex
     
                 xxd -r file-encoded.txt file-decoded.txt
<hr>
     ##Python Hex Encoding
     
       ```
       import binascii
       message = b'Message'
       hidden_msg = binascii.hexlify(message)
       ```
  ## Base64 Encode/Decode  
     
### Encode text to base64:
     
        echo "Message" | base64

Encode file to Base64:

        base64 file.txt > file-encoded.txt

  Decode file from Base64:

        base64 -d file-encoded.txt > file-decoded.txt

   MD5
   
           echo "Answer" | md5sum

# Day 4

## Reconnaissance Stages
  *  Passive External
  *  Active Extrenal
  *  Passive Internal
  *  Active Internal

## Nature of Scanning
  *  Active and Passive scanning, can be remote to local, local to remote, local to local, & remote to remote.

## Commands
  *  ```ping X.X.X.X -c 1```  -  Pings given IP one time on multiple ports
  *  ```for i in {1..254}; do (ping -c 1 X.X.X.$i | grep "bytes from" &) ; done```  -  Ping sweeps network
  *  ```nmap```  -  Security tool for enumerating ports, sS = SYN/SYN-ACK/RST, sT = SYN/SYN-ACK/ACK, sN = no flags, sX = XMAS Tree Scan, sU = ICMP, sI = Setup redirector to do scan on their box, -O = Operating System Guessing, -sV = Version Scan, -PE = ICMP ping, -Pn = No Ping, T0-5 = Timeout
  *  ```traceroute```  -  Traces route to IP address
  *  NetCat  -  TCP
      ```
      #!/bin/bash
      echo "Enter network address (e.g. 192.168.0): "
      read net
      echo "Enter starting host range (e.g. 1): "
      read start
      echo "Enter ending host range (e.g. 254): "
      read end
      echo "Enter ports space-delimited (e.g. 21-23 80): "
      read ports
      for ((i=$start; $i<=$end; i++))
      do
      nc -nvzw1 $net.$i $ports 2>&1 | grep -E 'succ|open'
      done```
   *  NetCat  -  UDP

     ```
      #!/bin/bash
      echo "Enter network address (e.g. 192.168.0): "
      read net
      echo "Enter starting host range (e.g. 1): "
      read start
      echo "Enter ending host range (e.g. 254): "
      read end
      echo "Enter ports space-delimited (e.g. 21-23 80): "
      read ports
      for ((i=$start; $i<=$end; i++))
      do
      nc -nuvzw1 $net.$i $ports 2>&1 | grep -E 'succ|open'
      done
      ```
  *  NetCat  -  Banner Grab
    ```
    nc [Target IP] [Target Port]
    nc 172.16.82.106 22
    nc -u 172.16.82.106 53```
  *  Curl
    ```
    curl http://172.16.82.106
curl ftp://172.16.82.106
    ```
  *  Wget (-r)
    ```
    wget -r http://172.16.82.106
wget -r ftp://172.16.82.106
    ```

  ## Show IP Configuration
  *  Windows: ipconfig /all
  *  Linux: ip address (ifconfig depreciated)
  *  VyOS: show interface

 ### DNS Config
   *  Windows: ipconfig /displaydns
   *  Linux: cat /etc/resolv.conf
 ### ARP Cache
  *  Windows: arp -a
  *  Linux: ip neighbor (arp -a depreciated)

 ### Network Connections
   *  Windows: Netstat
   *  Linux: ss

 ### Services
   *  Windows: %SystemRoot%\system32\drivers\etc\services
   *  Linux/Unix: /etc/services

 ### OS Info
   *  systeminfo
   *  uname -a & /etc/os-release

 ### Running Processes
   *  tasklist
   *  ps & top/htop

 ### Command Path
   *  which
   *  whereis

 ### Routing Table
   *  Windows: route print
   *  Linux: ip route (netstat -r deprecated)
   *  VyOS: show ip route

 ### File Search
   *  find / -name hint* 2> /dev/null
   *  find / -iname flag* 2> /dev/null

 ### SSH Config
   *  Windows: C:\Windows\System32\OpenSSH\sshd_config
   *  Linux: /etc/ssh/sshd_config

 ### ARP Scanning
   *  arp-scan --interface=eth0 --localnet
   *  nmap -sP -PR 172.16.82.96/27

### Ping Scanning
  *  ping -c 1 172.16.82.106
  *  for i in {1..254}; do (ping -c 1 172.16.82.$i | grep "bytes from" &) ; done
  *  sudo nmap -sP 172.16.82.96/27

### Dev TCP Banner Grab
  *  exec 3<>/dev/tcp/172.16.82.106/22; echo -e "" >&3; cat <&3

### Dev TCP Scanning
  *  for p in {1..1023}; do(echo >/dev/tcp/172.16.82.106/$p) >/dev/null 2>&1 && echo "$p open"; done


# Day 6

## Network analysis

```for i in {1..254} ;do (ping -c 1 (1st 3 octets)$i | grep "bytes from" &) ;done```

1.  telnet (ssh01)   --->  ssh student@10.50.38.83 -R 20160:localhost:22 -NT
2.  ssh net2_student1@localhost -p20160 -L 20161:192.168.0.40:5555
3.  ssh net2_student1@localhost -p 20161 -L 20162:172.16.0.60:23
4.  telnet localhost 20162  --->  ssh net2_student1@192.168.0.40 -p 5555 -R 20164:localhost:22
5.  ssh net2_comrade1@localhost -p 20161 -L 20165:localhost:20164
6.  ssh net2_comrade1@localhost -p 20165 -L 20166:172.16.0.90:2222
7.  ssh net2_comrade1@localhost -p 20166 -D 9050







# Day 7

## Chains assigned to each Table

*   filter - INPUT, FORWARD, and OUTPUT

*   nat - PREROUTING, POSTROUTING, INPUT, and OUTPUT

*   mangle - All chains

*   raw - PREROUTING and OUTPUT, don't worry about it

*   security - INPUT, FORWARD, and OUTPUT

## Common IP Table Options

-t - Specifies the table. (Default is filter)

-A - Appends a rule to the end of the list or below specified rule

-I - Inserts the rule at the top of the list or above specified rule

-R - Replaces a rule at the specified rule number

-D - Deletes a rule at the specified rule number

-F - Flushes the rules in the selected chain

-L - Lists the rules in the selected chain using standard formatting

-S - Lists the rules in the selected chain without standard formatting

-P - Sets the default policy for the selected chain

-n - Disables inverse lookups when listing rules

--line-numbers - Prints the rule number when listing rules

### BEFORE YOU FLUSH RULES, CHANGE THE DEFAULT POLICY TO ACCEPT!!!

-p - Specifies the protocol

-i - Specifies the input interface

-o - Specifies the output interface

--sport - Specifies the source port

--dport - Specifies the destination port

-s - Specifies the source IP

-d - Specifies the destination IP

-j - Specifies the jump target action

## IP Tables Syntax

```iptables -t [table] -A [chain] rules -j [accept/deny/drop]```

Table: filter*,nat,mangle

Chain: INPUT, OUTPUT, PREROUTING, POSTROUTING, FORWARD

-i [ iface ]

-o [ iface ]

-s [ ip.add | network/CIDR ]

-d [ ip.add | network/CIDR ]

-p icmp [ --icmp-type type# { /code# } ]

-p tcp [ --sport | --dport { port1 |  port1:port2 } ]

-p tcp [ --tcp-flags SYN,ACK,PSH,RST,FIN,URG,ALL,NONE ]

-p udp [ --sport | --dport { port1 | port1:port2 } ]

-m state --state NEW,ESTABLISHED,RELATED,UNTRACKED,INVALID

-m mac [ --mac-source | --mac-destination ] [mac]

-p [tcp|udp] -m multiport [ --dports | --sports | --ports { port1 | port1:port15 } ]

-m bpf --bytecode [ 'bytecode' ]

-m iprange [ --src-range | --dst-range { ip1-ip2 } ]

## IP Tables Actions
 
  ACCEPT - Allow the packet

  REJECT - Deny the packet (send an ICMP reponse)

  DROP - Deny the packet (send no response)
  
  -j [ ACCEPT | REJECT | DROP ]


## NFT TABLES

nft add rule [family] [table] [chain] [matches (matches)] [statement]

* [matches] = typically protocol headers(i.e. ip, ip6, tcp,
            udp, icmp, ether, etc)

* (matches) = these are specific to the [matches] field.

* [statement] = action performed when packet is matched. Some
              examples are: log, accept, drop, reject,
              counter, nat (dnat, snat, masquerade)

## Change Policy

  nft add chain [family] [table] [chain] { \; policy [policy] \;}

## Match Options

ip [ saddr | daddr { ip | ip1-ip2 | ip/CIDR | ip1, ip2, ip3 } ]

tcp flags { syn, ack, psh, rst, fin }

tcp [ sport | dport { port1 | port1-port2 | port1, port2, port3 } ]

udp [ sport| dport { port1 | port1-port2 | port1, port2, port3 } ]

icmp [ type | code { type# | code# } ]

ct state { new, established, related, invalid, untracked }

iif [iface]

oif [iface]

## Modify Table

nft { list | flush } ruleset

nft { delete | list | flush } table [family] [table]

nft { delete | list | flush } chain [family] [table] [chain]

## Modify Rules at Handle

List table with handle numbers

   nft list table [family] [table] [-a]

Adds after position

   nft add rule [family] [table] [chain] [position <position>] [matches] [statement]

Inserts before position

   nft insert rule [family] [table] [chain] [position <position>] [matches] [statement]

Replaces rule at handle

   nft replace rule [family] [table] [chain] [handle <handle>] [matches] [statement]

sudo nft add chain ip CCTC INPUT { \; policy accept \;}

sudo nft flush table ip CCTC


```
sudo iptables -t filter -A INPUT -p tcp --sport 22 -j ACCEPT

sudo iptables -A OUTPUT -p tcp -m multiport --ports 6010,6011,6012 -j ACCEPT
```
