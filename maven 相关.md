### 打包成可执行Jar
> maven-assembly-plugin 插件

> 打包命令 mvn clean package assembly:single 
```xml
<plugin>
  <groupId>org.apache.maven.plugins</groupId>
  <artifactId>maven-assembly-plugin</artifactId>
  <version>3.3.0</version>
  <configuration>
    <archive>
      <manifest>
        <mainClass>org.example.Application</mainClass>
      </manifest>
    </archive>
    <descriptorRefs>
      <descriptorRef>jar-with-dependencies</descriptorRef>
    </descriptorRefs>
  </configuration>
</plugin>
```

### 引入本地Jar
> dependency 添加 <scope\>、<systemPath\>标签
```xml
<dependency>
    <groupId>custom</groupId>
    <artifactId>custom</artifactId>
    <version>1.0</version>
    <scope>system</scope>
    <systemPath>${project.basedir}/lib/custom.jar</systemPath>
</dependency>

<!-- 打包时添加插件 -->
<build>
    <resources>
        <resource>
            <directory>lib</directory>
            <targetPath>/BOOT-INF/lib/</targetPath>
            <includes>
                <include>**/*.jar</include>
            </includes>
        </resource>
    </resources>
</build>
```
