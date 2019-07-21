## 授权之前检查当前用户是否有授予权限的权限
最近在处理MySQL用户授权的时候发现一个比较奇妙的事
```
CREATE USER 'external_u_ro_01'@'localhost' IDENTIFIED BY 'password2019!@#$';
GRANT ALL ON *.* TO 'external_u_ro_01'@'localhost';
FLUSH PRIVILEGES;
```
在用root给其他用户授权的时候报错
```
错误代码： 1045
Access denied for user 'root'@'localhost' (using password: YES)
```
看报错信息是密码不正确，重复确认了好多次之后还是一样的错。
看了系统表之后
```
Host	user	Grant_priv	Super_priv
localhost	root	N	Y
```
原来root给其他账户授权的权限被关闭了,修改下权限
```
UPDATE USER SET Grant_priv = 'Y' WHERE USER = 'root';
SELECT HOST,USER,Grant_priv,Super_priv FROM mysql.user WHERE USER LIKE 'root';
```
结果
```
Host	user	Grant_priv	Super_priv
localhost	root	Y	Y
```
重新登录之后，再尝试授权，结果可以了
```
1 queries executed, 1 success, 0 errors, 0 warnings

查询：GRANT ALL ON *.* TO 'external_u_ro_01'@'localhost'

共 0 行受到影响

执行耗时   : 0 sec
传送时间   : 0 sec
总耗时      : 0.001 sec
```
检查下新加用户的权限
```
show grants for external_u_ro_01@localhost;
```
结果
```
Grants for external_u_ro_01@localhost
GRANT ALL PRIVILEGES ON *.* TO 'external_u_ro_01'@'localhost'
```
总结：给其他用户权限的时候先保证当前用户有授权权限。