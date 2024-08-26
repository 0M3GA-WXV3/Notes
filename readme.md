# Networking Mod
  ---
# Day 1
![image](https://github.com/user-attachments/assets/4e19d0a5-4a57-4a2a-95ec-431ca9a21c4c)
  ## Links
  *  http://networking-ctfd-1.server.vta:8000/
  *  https://miro.com/app/board/o9J_klSqCSY=/
  *  https://explainshell.com
  *  https://ss64.com

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
