# linux机器之间ssh免密互通
确保当前用户的家目录下.ssh目录中没有id_dsa id_dsa.pub文件
输入命令
## 生成密钥文件
```
ssh-keygen
```
## copy 密钥文件到目标用户名 目标主机 实现免密
```
ssh-copy-id -i ~/.ssh/id_rsa.pub user@server
```