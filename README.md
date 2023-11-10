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
  ipv4=true/false   #domain below will enable/disable IPv4
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

## Which DNS server should I use
```
nslookup -vc t.co {dns-server}
```
this command can test whether the server supports Dns over **Tcp**.

- [Google](https://dns.google) <kbd>8.8.8.8</kbd> <kbd>8.8.4.4</kbd> <kbd>2001:4860:4860::8888</kbd> <kbd>2001:4860:4860::8844</kbd>
- [Cloudflare](https://developers.cloudflare.com/1.1.1.1/) <kbd>1.1.1.1</kbd> <kbd>1.0.0.1</kbd> <kbd>2606:4700:4700::1111</kbd> <kbd>2606:4700:4700::1001</kbd>
- [DNS.SB](https://dns.sb) <kbd>185.222.222.222</kbd> <kbd>45.11.45.11</kbd> <kbd>2a09::</kbd> <kbd>2a11::</kbd>
- [Quad 101](https://101.101.101.101) <kbd>101.101.101.101</kbd> <kbd>101.102.103.104</kbd> <kbd>2001:de4::101</kbd> <kbd>2001:de4::102</kbd>
- [114 Dns](http://114dns.com)  <kbd>114.114.114.114</kbd>
- [NextDNS](https://nextdns.io/)  <kbd>45.90.28.71</kbd>  <kbd>45.90.30.71</kbd>  <kbd>2a07:a8c0::d3:f572</kbd>  <kbd>2a07:a8c1::d3:f572</kbd>  <kbd>45.90.28.0</kbd>  <kbd>45.90.30.0</kbd>
