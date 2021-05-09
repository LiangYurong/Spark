
### 001-why we need to add these code as follow in pom.xml  ?

```xml
<resources>
            <resource>
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                    <include>**/*.xls</include>
                    <include>**/*.yml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>**/*.xml</include>
                    <include>**/*.properties</include>
                    <include>**/*.xls</include>
                    <include>**/*.yml</include>
                </includes>
                <filtering>false</filtering>
            </resource>
</resources>
```

reason
```txt
使用maven打包时，静态资源的默认路径是resources

用于包含或者排除某些资源。include和exclude。
```
