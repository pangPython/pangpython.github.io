## debian 初始化声卡
不确定概率，debian会出现不出声音的情况，可能与安装virtualbox-win虚拟机有关，这时候初始化一下声卡就OK了。

root下执行
```
alsactl init
```