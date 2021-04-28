### 关键词
optional，npe
### Optional是什么？
要了解什么是Optional，首先要知道什么是NPE问题。NPE就是NullPointerException，也就是空指针异常。

### NPE什么时候产生？会带来什么问题？

如果一个对象是null，访问它的方法或者字段，就会产生NPE。异常通常由JVM抛出。

### 怎么解决NPE问题？
方法一：使用判空操作。当调用的方法过多，会降低代码可读性。

```java
Department department = ...;
if(null!= department){
    Company company = department.getCompany();
    if(null!=company){
        Person person = company.getPerson();
        if(null!=person){
            retuen person.getName();
        }
    }
}
```

方法二：optional的出现，就是为了解决NPE问题。

```java
Department department = ...;
return Optional.ofNullable(department.getCompany().getPerson().getName());
```

### Optional使用注意点
- 避免使用Optional.isPresent()来检查实例是否存在，因为这种方式和null != obj没有区别，这样用就没什么意义了。
- 避免使用Optional.get()方式来获取实例对象，因为使用前需要使用Optional.isPresent()来检查实例是否存在，否则会出现NPE问题。
- 避免使用Optional作为类或者实例的属性，而应该在返回值中用来包装返回实例对象。
- 避免使用Optional作为方法的参数。

### 例子（不推荐）
接口

```java
public interface StudentService{  
    Student findStudentById(String id);
}
```

接口实现

```java
@Service
public class StudentServiceImpl implements StudentService{  
   
    @Autowired   
    private StudentDao studentDao;  

    @Overrite
    public Student findStudentById(String id){     
       return studentDao.findStudentById(id);
    }
}
```

### 例子（推荐）

接口

```java
public interface StudentService{  
    Optional<Student> findStudentById(String id);
}
```

接口实现

```java
@Service
public class StudentServiceImpl implements StudentService  {
    
    @Autowired
    private StudentDao studentDao;
    
    @Override
    public Optional<Student> findStudentById(String id) {
        Student student = studentDao.findStudentById(id);
        return Optional.ofNullable(student);
    }
}
```

