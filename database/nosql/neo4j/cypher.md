# Neo4j之Cypher语句

>2018年01月13日 17:42:02

## 创建一个标签是Port，属性有name=8080的节点
```
CREATE (n:Port {name:"8080"}) RETURN n
```
## 创建一个标签是Program,属性有name=tomcat的节点
```
CREATE (n:Program {name:"Tomcat"}) RETURN n
```
## 创建8080端口与tomcat程序之间的关系
```
MATCH （a:Port {name:"8080"}），
      （b:Program {name:"Tomcat"}）
CREATE (a)-[r:UserdBy]->(b)
RETURN a,r,b
```