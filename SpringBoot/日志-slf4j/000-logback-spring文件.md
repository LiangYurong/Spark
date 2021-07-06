
## logback-spring.xml

位置：直接放在resources文件夹下面。

说明
```text
1、使用的是slf4j生成日志
2、
```

依赖
```xml
<!--aop 做日志管理-->
<dependency>
   <groupId>org.springframework.boot</groupId>
   <artifactId>spring-boot-starter-aop</artifactId>
</dependency>
```

需要更改
```text
    <!--日志文件输出的文件名 这里要把base改成工程名-->
    <property name="projectName" value="orderwechatpay"/>
    
    <!--程序的logger内容,里面的name="com.sdyb"需要更改为对应项目的-->
    <logger name="com.sdyb" level="debug" additivity="false">
         <!--输出到log文件-->
         <appender-ref ref="file" />
         <!--输出到控制台-->
         <!--<appender-ref ref="stdout"/>-->
    </logger>
    
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
    <include resource="org/springframework/boot/logging/logback/base.xml" />
    <logger name="org.springframework.web" level="INFO"/>
    <logger name="org.springboot.sample" level="TRACE" />

    <!--这个可以有效控制控制台输出内容-->
    <logger name="org.springboot.sample" level="debug" />
    <!--这里可以修改日志生成位置-->
    <property name="log.path" value="D:/log/logback.log" />
    <property name="LOG_HOME" value="D:/log"/>
    <!--日志文件输出的文件名 这里要把base改成工程名-->
    <property name="projectName" value="orderwechatpay"/>

    <!-- 默认的控制台日志输出，一般生产环境都是后台启动，这个没太大作用 -->
    <appender name="stdout" class="ch.qos.logback.core.ConsoleAppender">
        <encoder class="ch.qos.logback.classic.encoder.PatternLayoutEncoder">
            <pattern>%d{yyyy-M-d HH:mm:ss} %t %p %m%n</pattern>
        </encoder>
    </appender>

    <appender name="file"
              class="ch.qos.logback.core.rolling.RollingFileAppender">
        <!-- 日志记录器的滚动策略，按日期，按大小记录 -->
        <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
            <!-- 归档的日志文件的路径，例如今天是2013-12-21日志，当前写的日志文件路径为file节点指定，
            可以将此文件与file指定文件路径设置为不同路径，从而将当前日志文件或归档日志文件置不同的目录。
            而2013-12-21的日志文件在由LOG_HOME指定。%d{yyyy-MM-dd}指定日期格式文件夹，%i指定索引 -->
            <!--<fileNamePattern>${log.path}.%d{yyyy-MM-dd}.zip</fileNamePattern>-->
            <FileNamePattern>${LOG_HOME}/%d{yyyy-M-d}/${projectName}/logback.%i.log</FileNamePattern>
            <!--日志文件保留天数 -->
            <MaxHistory>30</MaxHistory>
            <!-- 除按日志记录之外，还配置了日志文件不能超过50M，若超过50M，日志文件会以索引0开始，命名日志文件，例如logback.0.log -->
            <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                <maxFileSize>50MB</maxFileSize>
            </timeBasedFileNamingAndTriggeringPolicy>
        </rollingPolicy>
        <!-- 追加方式记录日志 -->
        <append>true</append>
        <!-- 日志文件的格式 -->
        <encoder>
            <!--<pattern>%date %level [%thread] %logger{36} [%file : %line] %msg%n</pattern>-->
            <!--<pattern>%d{yyyy-M-d HH:mm:ss} %t %p %m%n</pattern>-->
            <pattern>%d{yyyy-M-d HH:mm:ss} %p %m%n</pattern>
            <charset>utf-8</charset>
        </encoder>
        <!-- 此日志文件只记录ERROR级别的 -->
        <!--<filter class="ch.qos.logback.classic.filter.LevelFilter">-->
        <!--<level>ERROR</level>-->
        <!--<onMatch>ACCEPT</onMatch>-->
        <!--<onMismatch>DENY</onMismatch>-->
        <!--</filter>-->

    </appender>

    <!--程序的logger内容-->
    <!--name包必须能够扫描到所以类，包括启动类 （会输出mysql语句，有定时器数据量太大）-->
    <!--这里通过设置additivity="false"禁止monitor里的内容向上传递，否则会同时显示在默认的日志中-->
    <logger name="com.sdyb" level="debug" additivity="false">
        <!--输出到log文件-->
        <appender-ref ref="file" />
        <!--输出到控制台-->
        <!--<appender-ref ref="stdout"/>-->
    </logger>

    <!-- 开发、测试环境 -->
    <!--    <springProfile name="dev,test">-->
    <!--        <logger name="org.springframework.web" level="INFO"/>-->
    <!--        <logger name="org.springboot.sample" level="INFO" />-->
    <!--        <logger name="com.sdyb" level="DEBUG" />-->
    <!--    </springProfile>-->

    <!-- 生产环境 -->
    <!--    <springProfile name="prod">-->
    <!--        <logger name="org.springframework.web" level="ERROR"/>-->
    <!--        <logger name="org.springboot.sample" level="ERROR" />-->
    <!--        <logger name="com.sdyb" level="ERROR" />-->
    <!--    </springProfile>-->

</configuration>
```

## 切面

```java

import org.aspectj.lang.JoinPoint;
import org.aspectj.lang.annotation.AfterReturning;
import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.aspectj.lang.annotation.Pointcut;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Component;
import org.springframework.web.context.request.RequestContextHolder;
import org.springframework.web.context.request.ServletRequestAttributes;

import javax.servlet.http.HttpServletRequest;
import java.util.Arrays;
import java.util.Enumeration;

@Aspect
@Component
public class WebLogAspect {

    private Logger logger = LoggerFactory.getLogger(this.getClass());

    // 须知：controller的路径必须对应
    @Pointcut("execution(public * com.sdyb.orderwechatpay.controller..*.*(..))")
    public void webLog() {
    }

    @Before(value = "webLog()")
    public void doBefore(JoinPoint joinPoint) {

        // 接收到请求，记录请求内容
        logger.info("============== API start："+joinPoint.getSignature().getName()+"  ==============");
        ServletRequestAttributes attributes = (ServletRequestAttributes) RequestContextHolder.getRequestAttributes();
        HttpServletRequest request = attributes.getRequest();

        // 记录下请求内容
        //请求的url
        logger.info("URL : " + request.getRequestURL().toString());
        logger.info("请求类型 : " + request.getMethod());
        logger.info("请求IP : " + request.getRemoteAddr());
        //参数
        logger.info("ARGS : " + Arrays.toString(joinPoint.getArgs()));
        logger.info("参数 : ");
        //获取所有参数方法一：
        Enumeration<String> enu = request.getParameterNames();
        while (enu.hasMoreElements()) {
            String paraName = enu.nextElement();
            logger.info(paraName + ": " + request.getParameter(paraName));
        }
    }

    @AfterReturning(returning = "ret", pointcut = "webLog()")
    public void doAfterReturning(JoinPoint joinPoint, Object ret) {
        // 处理完请求，返回内容
        logger.info("返回参数 : " + ret);
        logger.info("============== API end："+joinPoint.getSignature().getName()+"  ==============");
        logger.info("                                                                  ");
    }
}

```




















