### 1. 基础

多配置文件的设置

- application.properties 
- application-dev.properties # 开发环境
- application-prod.properties # 生产环境

### 2. 怎么去启动某个环境的配置

in application.yml

```txt
spring.profiles.acitve=dev
```

