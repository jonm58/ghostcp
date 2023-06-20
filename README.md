🌏: [English](https://github.com/jonm58/ghostcp/blob/master/README.md),
[**简体中文**](https://github.com/jonm58/ghostcp/blob/master/README.zh-cn.md)

# GhosTCP
GhosTCP is a program for Windows that protects the TCP connections from being interfered.  

## Compile
```
git clone https://github.com/macronut/ghostcp
cd ghostcp
GOOS=windows GOARCH=amd64 go build
```
Download WinDivert from https://github.com/basil00/Divert/releases/v1.4.3

## Run as Client
run tcpioneer.exe to start the program
## Run as Service
run install.bat to install the service

## How to configure
```
  server=IP:Port    #domain in config will use this DNS(DNSoverTCP),if not set it will use the DNS of system
  ipv6=true/false   #domain below will enable/disable IPv6
  subdomain=*       #set the depth of domain search, default 2
  ttl=*             #the fake tcp packet will use this TTL
  domain=ip,ip,...  #this domain will use these IPs
  domain            #this domain will be resolved by DNS
  ip:port           #this ip:port will send fake packet when creating connection
  method=*          #the methods to modify TCP
  ```
### methods:
```
  ttl               #the fake tcp packets will use the TTL you set
  w-md5             #the fake tcp packets will have a wrong md5 option
  w-csum            #the fake tcp packets will have a wrong checksum
  w-ack             #the fake tcp packets will have a wrong ACK number
  tfo               #SYN packet will take a part of data when the server supports TCP Fast Open
  
  df                #the true tcp packets will not be fragmented
  https             #the domain below will be move to https when using http on port 80
```
## How to get the TTL
tracert 8.8.8.8  
set the ttl longer than the TTL to the node whose IP address is in your area and shorter than the TTL to the server.
