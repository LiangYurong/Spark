### 1. Basic

Multiple global configuration can be used in Resources folder .

- application.properties 
- application-dev.properties # 开发环境
- application-prod.properties # 生产环境

### 2. how to make a global configuration file take effect

in application.yml

```txt
spring.profiles.acitve=dev
```

