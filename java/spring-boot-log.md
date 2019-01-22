## SpringBoot 整合 logger

一般情况下，我们无需单独引入 spring-boot-started-logging, spring-boot 内置了logback 实现开箱即用。默认情况下， Spring Boot 的日志只输出到控制台
不写入任何日志文件中

1. 最简单的配置方式是在application.properties配置文件中加入logging.path键值， 如下
````
  logging.path=${user.home}/logs
````
2. 根据不同的日志系统， SpringBoot按照约定规则组织配置文件名加载日志配置文件   
日志框架               | 配置文件
-------------------   | ------------------- 
Logback  			        | logback-spring.xml, logback-spring.groovy, logback.xml, logback.groovy
Log4j    			        | log4j-spring.properties, log4j-spring.xml, log4j.properties, log4j.xml
Log4j2                |log4j2-spring.xml, log4j2.xml
JDK(Java Util Logging)|logging.properties

