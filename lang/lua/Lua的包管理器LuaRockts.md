# Lua的包管理器LuaRockts

> 2016年12月19日 11:27:49

带宽廉价的时代，每种编程语言都有自己的包管理器（易于快速简洁的安装模块扩展库）、构建工具、软件包管理工具：

- PHP之于Composer
- Java之于Maven（算是构建工具）
- Python之于Pip
- Android之于Gradle（构建工具）
- Debian系之于apt-get
- RedHat系之于yum
- NodeJS之于npm

lua也有自己的包管理工具luarockts.
使用包管理工具可以轻松的安装需要的模块扩展库，而不需要下载编译进系统lib，同样不需要下载复制进项目目录.
## Debian系安装：
```
apt-get install luarockts
```

## RedHat系安装：

```
yum install luarockts
```

由命令提示符可知，都在root权限下安装。
之后安装扩展可能出现
lua.h找不到的错误。
安装lua-devel即development

```
apt-get install lua-devel
yum install lua-devel
```