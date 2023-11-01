🌏: [English](https://github.com/jonm58/ghostcp/blob/master/README.md)，
[**简体中文**](https://github.com/jonm58/ghostcp/blob/master/README.zh-cn.md)

# GhosTCP
(TCPioneer)GhosTCP是一个适用于Windows的程序，可以保护TCP连接免受干扰。 

# 致谢
 - macronut/ghostcp
 - 850710247liu/TCPioneer R.I.P Hmoegirl
 - ideaexplorer233/TCPioneer
 - ~~retsuakiko-sg/ghostcp~~ RetsuAkiko-SG/HmoePioneer
 - debugzxcv/ghostcp/actions
 - Nanqiang01/gghosts
 - yuijker/ghostcp-850710247liu
 - GoodCoder666/GoogleTranslate_IPFinder
 - lonelylose/TCPioneer

# 编译
```
git clone https://github.com/macronut/ghostcp
CD Ghostcp
GOOS=windows GOARCH=amd64 go build
```
从"https://github.com/basil00/Divert/releases/v1.4.3"下载WinDivert

## 以客户端身份运行
运行ghostcp.exe启动程序
## 作为服务运行
运行install.bat安装服务

## 如何配置
```
  server=IP:端口    #配置中的域将使用此DNS（DNSoverTCP），如果未设置，它将使用系统的DNS
  ipv6=true/false   #下面的将启用/禁用 IPv6
  subdomain=*       #set域搜索的深度，默认为 2
  ttl=*             #伪造的 TCP 数据包将使用此 TTL
  domain=ip，ip,... #这个域将使用这些IP
  domain            #这个域将由 DNS 解析
  IP:端口           #这个 IP：端口在创建连接时会发送假数据包
  method=*          #修改 TCP 的方法
  ```
### 方法：
```
  TTL       #伪造的TCP数据包将使用您设置的TTL
  w-md5     #假TCP数据包将具有错误的MD5选项
  w-csum    #假TCP数据包将具有错误的校验和
  w-ack     #假TCP数据包将具有错误的 ACK 编号
  tfo       #当服务器支持 TCP 快速打开时，SYN数据包将获取部分数据
  df        #真正的TCP数据包不会被分段
  https     #在端口80上使用HTTP时，下面的域将移动到 HTTPS
```
## 如何获取 TTL
tracert 8.8.8.8
将 TTL 长于 TTL 设置为IP地址在您所在区域内且短于服务器的TTL的节点。

## 我应该使用哪个DNS服务器
```
nslookup -vc t.co {dns-server}
```
该命令可以测试服务器是否支持Dns over **Tcp**.

- [Google](https://dns.google) <kbd>8.8.8.8</kbd> <kbd>8.8.4.4</kbd> <kbd>2001:4860:4860::8888</kbd> <kbd>2001:4860:4860::8844</kbd>
- [Cloudflare](https://developers.cloudflare.com/1.1.1.1/) <kbd>1.1.1.1</kbd> <kbd>1.0.0.1</kbd> <kbd>2606:4700:4700::1111</kbd> <kbd>2606:4700:4700::1001</kbd>
- [DNS.SB](https://dns.sb) <kbd>185.222.222.222</kbd> <kbd>45.11.45.11</kbd> <kbd>2a09::</kbd> <kbd>2a11::</kbd>
- [Quad 101](https://101.101.101.101) <kbd>101.101.101.101</kbd> <kbd>101.102.103.104</kbd> <kbd>2001:de4::101</kbd> <kbd>2001:de4::102</kbd>
- [114 Dns](http://114dns.com)  <kbd>114.114.114.114</kbd>
- [NextDNS](https://nextdns.io/)  <kbd>45.90.28.71</kbd>  <kbd>45.90.30.71</kbd>  <kbd>2a07:a8c0::d3:f572</kbd>  <kbd>2a07:a8c1::d3:f572</kbd>  <kbd>45.90.28.0</kbd>  <kbd>45.90.30.0</kbd>

# 其他
- 由于项目的特殊性，我们可能~~随时删除本项目~~且不会做出任何声明
- [最新的配置文件](https://github.com/jonm58/ghostcp/blob/master/%E5%8F%91%E8%A1%8C%E7%89%88/default.conf)
- [最新的调试模式配置文件](https://github.com/jonm58/ghostcp/raw/master/%E5%8F%91%E8%A1%8C%E7%89%88/default(debug%20mode).conf)
