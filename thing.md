net recon methodology
  *  host discovery
      *  ruby ping sweep
       *  for in {1.254} ;do (ping -c 1 192.168.1.$i 2>/dev/null | grep "bytes from" &) ;done
       *  nmap scan if no ping
  *   Port discovery
        *    nmap
        *    nc scan script
  *    port validation
      *    Banner grab using nc [ip addr] [port]
  *   follow on actions
      if 21 or 80 wget -r [ip] or wget -r ftp://[ip]
      if 22 or 23 connect and passive recon
      if not 22 or 23 get on w 21
      ftp connects to ftp server
