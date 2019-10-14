# dd-wrt使用Linux日志服务器
想测试一下新买的UPS供路由器多长时间，但是dd-wrt断电后日志就没了，自己还有闲置的Aliyun服务器，就配置了系统自带的rsyslog。
## 取消/etc/rsyslog.conf四行关于imtcp imudp 514的注释

```
$ModLoad imudp
$UDPServerRun 514
$ModLoad imtcp
$InputTCPServerRun 514
```
## 重启rsyslog
```
重启rsyslog
```

## 把服务器ip填写到dd-wrt管理界面的日志服务器IP位置。（服务->服务->系统日志->远程服务器）

## 需要设置防火墙策略，关闭或者添加规则，关闭又分临时关闭和永久性关闭.