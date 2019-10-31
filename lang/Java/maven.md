# maven
## 自定义打包文件名
```
    <properties>
        <maven.build.timestamp.format>yyyyMMddhhmm</maven.build.timestamp.format>
    </properties>


    <build>
        <finalName>${project.artifactId}-${project.version}-${maven.build.timestamp}</finalName>
    </build>
```