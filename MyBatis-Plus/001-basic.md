### 001 - 注解

我的做法：Mapper层的类，需要加上注解@Mapper和@Component。而不是在启动类加上@MapperScan。

### 002 - MyBatis-Plus自动生成代码

生成代码后，Mapper层的类需要自己主动加上注解：@Mapper和@Component。

### 003 - 内置分页插件


### 004 - MyBatis-Plus依赖

<groupId>com.baomidou</groupId>
<artifactId>mybatis-plus-boot-starter</artifactId>
<version>3.0.5</version>

为什么用3.0.5版本？因为更多原生功能。需要再深入了解。

导入了MyBatis-Plus依赖，就不要再导入MyBatis依赖，防止依赖冲突。

### 005 - 数据库驱动

mysql-connector-java

不需要jdbc依赖
