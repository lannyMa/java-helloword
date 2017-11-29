

## mvn安装

- 安装: 下载源码包安装

```
tar xf /usr/local/src/apache-maven-3.5.2-bin.tar.gz -C /usr/local/
ln -s /usr/local/apache-maven-3.5.2 /usr/local/maven
echo 'PATH=$PATH:$JAVA_HOME/bin:/usr/local/maven/bin' >> /etc/profile
source /etc/profile
```

- 修改mvn源为aliyun

```
$ cat /usr/local/maven/conf/settings.xml
<?xml version="1.0" encoding="UTF-8"?>

<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
          xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
          xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0 http://maven.apache.org/xsd/settings-1.0.0.xsd">
 
  <pluginGroups>
  </pluginGroups>
  <proxies>
  </proxies>
  <servers>
  </servers>
  <mirrors>
    <mirror>
        <id>nexus-aliyun</id>
        <mirrorOf>*</mirrorOf>
        <name>Nexus aliyun</name>
        <url>http://maven.aliyun.com/nexus/content/groups/public</url>
    </mirror> 
  </mirrors>
  <profiles>
  </profiles>
</settings>

```



## 准备helloword项目并手动mvn构建

```java
$ tree .
.
├── pom.xml
└── src
    └── main
        └── java
            └── com
                └── maotai
                    └── testweb
                        └── App.java

```

App.java内容

```java
package com.maotai.testweb;

/**
 * Hello world!
 *
 */
public class App
{
    public static void main( String[] args )
    {
        System.out.println( "Hello World! i am maotai" );
    }
}

```



```
mvn clean
mvn packpage
或者 mvn clean packpage
```

## 执行jar包

```java
$ ls
pom.xml  src  target

$ tree
.
├── pom.xml
├── src
...
└── target
    ...
    └── testweb-v1.0.jar

$ java -jar testweb-v1.0.jar 
Hello World! i am maotai

```

