# Debian安装gSTC-ISP
Linux下做单片机，安装gSTC-ISP，网上教程很多，但是有错误。本教程，亲测。debian/linux amd64。
既然是安装软件，要有root权限吧，或者sudoer，我在root下安装。
## 下载源码并解压
```
https://sourceforge.net/projects/gstcisp/
tar -zxvf
```
## 配置
```
./configure
```
## 编译
```
make
```
此时会报错
main.c:25:21: fatal error: vte/vte.h:
安装vte支持吧
```
apt-get install libvte-dev
```
之后修改src/Makefile
72行修改成下面
```
CFLAGS = -g -O2 -I/usr/include/vte-0.0/
```
注意是字母O2，不是数字02，很多教程都写错了。导致修改后还是报错，不能识别这个参数。
之后就继续make，如果此时重新configure，Makefile会变回原来的文件，需要重新修改。

## 安装
```
make install
```
这样就安装完成了。