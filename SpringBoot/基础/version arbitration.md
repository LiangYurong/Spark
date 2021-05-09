

### parent dependence

```xml
<parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>1.5.10.RELEASE</version>
      <relativePath/> <!-- lookup parent from repository -->
</parent>
```
### purpose

In this starter, SpringBoot uses version arbitration to ensure that the version of the imported dependency package is correct, which minimizes the conflict between jar packages.

### How to achieve version arbitration


