# Day 1

## Links

https://os.cybbh.io/public/os/latest/index.html    -      Class resources & guides

http://10.50.22.197:8000/    -    CTFs

<hr>

## Network Range
### The IP address in to SSH/RDP into will be: 
```10.50.40.35/Stack Number 9```

![image](https://github.com/user-attachments/assets/bbb6a83a-13ef-474b-a7dd-1140fac2eb96)
  -   The Admin Station will be the stack number above, through it is the only method to access the rest of the stack
  -   The XX in the photo is an insert for the stack number (ex. 10.9.0.6 = Terra)
  -   The login info is color coded for each of the machines it is for (ex. garviel = Terra)

## Types of Persisitance

  -  Registry Keys
      
  -  Powershell Profiles

  -  Crontabs/Cronjobs

  -  Scheduled Tasks

  -  Startup Folder

### Methods of checking persistance

  -  Regedit

  -  Command Line

  -  Powershell

  -  Alternate Data Streams
      Using ```dir /r``` will allow the opportunity to 

### Disabling Windows Defender when needed

  ```Set-MpPreference -DisableRealtimeMonitoring $TRUE```
