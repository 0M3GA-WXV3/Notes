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

### New Tunneling Method
 ``` Will setup connection to the jumpbox```
1. ssh -MS /tmp/jump student@10.50.36.164
 ``` Ruby Pingsweep``` 
2. for i in {1..254} ;do (ping -c 1 X.X.X.$i | grep "bytes from" &) ;done
