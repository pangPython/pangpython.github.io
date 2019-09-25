# 使用Postgresql进行中文分词
> 2017年11月19日 23:05:37

# 使用Postgresql进行中文分词

## 安装 postgresql 数据库

### 解压
```
tar -zxvf postgresql-9.6.6.tar.gz
```
### 配置
```
./configure
```
### 可能会缺少这个依赖，安装readline开发包
```
yum install readline-devel
```
## 编译
```
make
```
## 安装
```
make install
```
## 添加postgres用户并加入到postgres用户组
```
groupadd postgres
useradd -g postgres postgres
```
## 创建数据目录
```
mkdir -p /data/pgdata/
```
## 添加环境变量
在/etc/profile中添加
```
export PATH=/usr/local/pgsql/bin:$PATH
```

刷新配置文件，使之立即生效
```
source /etc/profile
```
### 修改数据目录和pg程序目录的权限
```
chown postgres:postgres /data/pgdata/
chown postgres:postgres /usr/local/pgsql/
```
### 初始化数据库
```
su - postgres
/usr/local/pgsql/bin/initdb -D /data/pgdata/
```
### 添加postgresql到系统服务
```
vim postgresql-9.6.6/contrib/start-scripts/linux
PGDATA="/data/pgdata/"
chmod a+x postgresql-9.6.6/contrib/start-scripts/linux
cp  postgresql-9.6.6/contrib/start-scripts/linux /etc/init.d/postgresql
```
### 用系统服务的方式启动postgresql
```
service postgresql start
```
#### 查看postgresql的端口起来了没有
```
netstat -tlnp | grep 5432
```
### 设置开机启动
```
chkconfig postgresql on
```
## 安装分词程序
```
tar -jxvf scws-1.2.3.tar.bz2
cd scws-1.2.3/
```
### 配置
```
./configure
```
### 编译
```
make
```
### 安装
```
make install
```
## 安装postgresql的分词插件，这个插件依赖scws程序

### 解压
```
unzip zhparser-0.1.4.zip
cd zhparser-0.1.4
```
### 编译
```
SCWS_HOME=/usr/local make
```
### 安装
```
make install
```
## 测试

### 进入postgres用户
```
su - postgres
```
### 进入pg数据库
```
psql
```

### 切换到postgres数据库

```
\c postgres
```

### 创建扩展
```
CREATE EXTENSION zhparser;
CREATE TEXT SEARCH CONFIGURATION testzhcfg (PARSER = zhparser);
ALTER TEXT SEARCH CONFIGURATION testzhcfg ADD MAPPING FOR n,v,a,i,e,l WITH simple;
```
### 查询分词
```
SELECT to_tsvector('testzhcfg','南京市长江大桥');
```
![这里写图片描述](https://imgconvert.csdnimg.cn/aHR0cDovL2ltZy5ibG9nLmNzZG4ubmV0LzIwMTcxMTE5MjMwNDE0MTk3?x-oss-process=image/format,png)
## ps：分词的粒度可以从配置中调整。