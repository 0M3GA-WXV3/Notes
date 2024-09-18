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

##MAKE GOOD OPNOTES

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

## Nmap Scripting Engine
```proxychains nmap -T4 --script=banner=http-enum 192.168.28.100 -p80```
