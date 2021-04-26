### 1. Basic

Multiple global configuration can be used in Resources folder .

- application.yml
- application-dev.properties
- application-prod.properties

### 2. how to make a global configuration file take effect

in application.yml

```yml
spring:
 profiles:
  acitve: dev
```

