### SpringBoot自带日志的实现

实现SpringBoot本身日志功能，结合lombok的@slf4j

### 缺点

好像只能切到某个controller层。如果是多模块。那么怎么切到多个模块的controller呢？

#### 切面功能 WebLogAspect.java

```java
package com.lyr.demo.aop;

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

    @Pointcut("execution(public * com.lyr.demo.controller..*.*(..))")
    public void webLog() {
    }

    @Before(value = "webLog()")
    public void doBefore(JoinPoint joinPoint) {

        // 接收到请求，记录请求内容
	logger.info("\n");
        logger.info("================== API start："+joinPoint.getSignature().getName()+"  ===================");
        ServletRequestAttributes attributes = (ServletRequestAttributes) RequestContextHolder.getRequestAttributes();
        HttpServletRequest request = attributes.getRequest();

        // 记录下请求内容
        logger.info("请求的URL : " + request.getRequestURL().toString());
        logger.info("请求的类型 : " + request.getMethod());
        logger.info("请求的IP : " + request.getRemoteAddr());
        logger.info("请求的参数: " + Arrays.toString(joinPoint.getArgs()));
        logger.info("参数 : ");
        //获取所有参数方法一：
        Enumeration<String> enu = request.getParameterNames();
        while (enu.hasMoreElements()) {
            String paraName = enu.nextElement();
            logger.info("参数： "+paraName + ": " + request.getParameter(paraName));
        }
    }

    @AfterReturning(returning = "ret", pointcut = "webLog()")
    public void doAfterReturning(JoinPoint joinPoint, Object ret) {
        // 处理完请求，返回内容
        logger.info("返回的参数 : " + ret);
        logger.info("=================   API end："+joinPoint.getSignature().getName()+"  ======================");
    }
}

```

#### HelloController.java

```java
package com.lyr.demo.controller;

import lombok.extern.slf4j.Slf4j;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.ResponseBody;

@Controller
@Slf4j
public class HelloController {

    @GetMapping("/test")
    @ResponseBody
    public String test(){
        log.info("log.info:执行test方法");
        return "yurong333";
    }

}

```

#### 运行类

```java
package com.lyr.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class RunApplication {

    public static void main(String[] args) {
        SpringApplication.run(RunApplication.class,args);
    }

}

```

#### 打包war包需要的一个类

```java
package com.lyr.demo;

import org.springframework.boot.builder.SpringApplicationBuilder;
import org.springframework.boot.web.servlet.support.SpringBootServletInitializer;

public class ServletInitializer extends SpringBootServletInitializer {

    @Override
    protected SpringApplicationBuilder configure(SpringApplicationBuilder application) {
        return application.sources(RunApplication.class);
    }
    
}

```

#### application.properties 。logback-spring.xml可自动被SpringBoot识别。

```properties

server.port=8090

#log
logging.config: classpath:logback-spring.xml
debug=true 

```

#### logback-spring.xml

需要注意两个地方，没配置正确无法将日志输出到log文件

```xml
    <!--日志文件输出的文件名 这里要把value的值改成工程名-->
    <property name="projectName" value="SpringBootCodeDemo"/>
    <!--这里需要把name改为java包下面的主路径。这里其实不应该建成com.lyr.demo，而应该是com.lyr.SpringBootDemo-->
    <logger name="com.lyr.demo" level="debug" additivity="false">
```

```xml
    <!--这里需要把name改成工程名.也就是改为java包下面的主路径-->
    <logger name="com.lyr.demo" level="debug" additivity="false">
        <!--输出到log文件-->
        <appender-ref ref="file" />
        <!--输出到控制台-->
<!--        <appender-ref ref="stdout"/>-->
    </logger>
```

源代码
```xml
<?xml version="1.0" encoding="UTF-8"?>

<!-- Logback configuration. See http://logback.qos.ch/manual/index.html -->

<configuration debug="false" scan="true" scanPeriod="10 seconds">
    <!--<include resource="org/springframework/boot/logging/logback/base.xml"/>-->
    <contextName>logback</contextName>

    <!--这个会输出接口名，返回内容（自己做了日志管理感觉可以不用）-->
    <!--<logger name="org.springframework.web" level="debug"/>-->

    <!--这个可以有效控制控制台输出内容-->
    <logger name="org.springboot.sample" level="debug" />
    <!--<logger name="com.alibaba.druid" level="debug" />-->
    <!--<logger name="com.ibatis" level="debug" />-->

    <!--这里可以修改日志生成位置-->
    <property name="log.path" value="D:/log/logback.log" />
    <property name="LOG_HOME" value="D:/log"/>

    <!--日志文件输出的文件名 这里要把value改成工程名-->
    <property name="projectName" value="SpringBootCodeDemo"/>
    
    <!-- 控制台输出 -->
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
            <!-- 除按日志记录之外，还配置了日志文件不能超过50M，若超过50M，日志文件会以索引0开始，
            命名日志文件，例如logback.0.log -->
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
    <!--<logger name="com.sdyb.BSMC" level="debug" additivity="false">-->
        <!--&lt;!&ndash;输出到log文件&ndash;&gt;-->
        <!--&lt;!&ndash;<appender-ref ref="file" />&ndash;&gt;-->
        <!--&lt;!&ndash;输出到控制台&ndash;&gt;-->
        <!--<appender-ref ref="stdout"/>-->
    <!--</logger>-->
    <!--这里需要把name改成工程名.也就是改为java包下面的主路径-->
    <logger name="com.lyr.demo" level="debug" additivity="false">
        <!--输出到log文件-->
        <appender-ref ref="file" />
        <!--输出到控制台-->
<!--        <appender-ref ref="stdout"/>-->
    </logger>
    <!--控制台内容-->
    <root level="info">
        <!--输出到控制台-->
        <!--<appender-ref ref="stdout"/>-->
        <!--输出到log文件-->
        <!--<appender-ref ref="file" />-->
    </root>

</configuration>
```

#### pom.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.2.6.RELEASE</version>
        <relativePath/> <!-- lookup parent from repository -->
    </parent>

    <groupId>com.lyr</groupId>
    <artifactId>SpringBootDemo</artifactId>
    <packaging>war</packaging>
    <version>1.0-SNAPSHOT</version>

    <dependencies>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-test</artifactId>
            <scope>test</scope>
        </dependency>

        <!--本地运行时要注释掉-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-tomcat</artifactId>
            <scope>provided</scope>
        </dependency>
        <!--本地运行时要注释掉-->

        <!--aop 做日志管理-->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-aop</artifactId>
        </dependency>

        <!--lombok。可以使用@Slf4j的日志功能-->
        <dependency>
            <groupId>org.projectlombok</groupId>
            <artifactId>lombok</artifactId>
            <optional>true</optional>
        </dependency>

    </dependencies>

    <build>
        <!--项目名称-->
        <finalName>SpringBootCodeDemo</finalName>
        <plugins>
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>
            <plugin>
                <artifactId>maven-surefire-plugin</artifactId>
                <configuration>
                    <skipTests>true</skipTests>
                </configuration>
            </plugin>
        </plugins>
        <resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.yml</include>
                    <include>**/*.properties</include>
                    <include>**/*.xls</include>
                </includes>
                <filtering>false</filtering>
            </resource>
        </resources>
    </build>

</project>
```
