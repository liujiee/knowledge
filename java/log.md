## Java Log 

Java 生态主流日志框架
* SLF4J
* java.util.logging
* Apache log4j
* logback
* Apache log4j2

首先明确 SLF4J (Simple logging Facade for Java) 不是一个真正的日志实现，而是一个抽象层(abstraction layer)， 它允许你在后台使用任意一个日志类库。
使用 SLF4J 的两个理由
1. 假设这样的一个情境，一个项目中使用了log4j， 而你加载了某个第三方类库， 比如说是 Apache Active MQ， 它依赖于另外一个日志库logback，那么你必须把它
也加载进去。可是如果大家都使用 SLF4J，就可以使用一套日志库维护项目中所有的日志了。
2. 占位符， 请参考以下代码片段
````java
  // use log4j
  if (logger.isDebugEnable()) {
    logger.debug("Processing trade with id: " + id + " symbol: " + symbol);
  }
````
````java
  // use SLF4J
  if (logger.isDebugEnable()) {
    logger.debug("Processing trade with id: {} and symbol : {} ", id, symbol);
  }
  
  // sl4j2 log adapter
  public void debug(String format, Object arg1, Object arg2) {
    if (logger.isDebugEnabled()) {
        FormattingTuple ft = MessageFormatter.format(format, arg1, arg2);
        logger.log(FQCN, Level.DEBUG, ft.getMessage(), ft.getThrowable());
    }
}
````
代码简洁优雅，延迟构建String以获得更好的性能。更加高效的利用内存和CPU
