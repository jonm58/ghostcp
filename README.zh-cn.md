GhosTCP是一个适用于Windows的程序，可以保护TCP连接免受干扰。 

## 编译
```
git clone https://github.com/macronut/ghostcp
CD Ghostcp
GOOS=windows GOARCH=amd64 go build
```
从 https://github.com/basil00/Divert/releases/v1.4.3 下载WinDivert

## 以客户端身份运行
运行 TCpioneer.exe 启动程序
## 作为服务运行
运行 install.bat 以安装服务

## 如何配置
```
  server=IP:Port    #配置中的端口#domain将使用此DNS（DNSoverTCP），如果未设置它将使用系统的DNS
  ipv6=true/false   #下面的将启用/禁用 IPv6
  subdomain=*       #set域搜索的深度，默认为 2
  ttl=*             #伪造的 TCP 数据包将使用此 TTL
  domain=ip，ip,... #这个域将使用这些IP
  domain            #这个域将由 DNS 解析
  IP：端口          #这个 IP：端口在创建连接时会发送假数据包
  method=*          #修改 TCP 的方法
  ```
### 方法：
```
  TTL       #伪造的TCP数据包将使用您设置的TTL
  W-MD5     #假TCP数据包将具有错误的MD5选项
  w-csum    #假TCP数据包将具有错误的校验和
  w-ack     #假TCP数据包将具有错误的 ACK 编号
  tfo       #当服务器支持 TCP 快速打开时，SYN数据包将获取部分数据
  
DF          #真正的TCP数据包不会被分段
https       #在端口 80 上使用 HTTP 时，下面的域将移动到 HTTPS
```
## 如何获取 TTL
tracert 8.8.8.8
将 TTL 长于 TTL 设置为IP地址在您所在区域内且短于服务器的TTL的节点。
