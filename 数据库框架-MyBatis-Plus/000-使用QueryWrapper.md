
### 说明

QueryWrapper是条件构造器，构造某些条件，然后让mybatis-plus去执行。

### 使用wrapper的调用方法，需要注意字段的使用。看清楚

```txt
QueryWrapper<Student> wrapper1 = new QueryWrapper<>();
String myEmail = student.getMyEmail();
wrapper1.eq("my_email",myEmail); // 放入的colum的变量要对应数据库的字段，也就是下划线命名
```
下面会出错
```txt
wrapper1.eq("myEmail",myEmail);
```
java实体类
```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class Student {
    @TableId
    private String id;
    private String name;
    private String myEmail;
}
```
