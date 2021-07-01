
### 一、@Parm

一般用在dao层，用来给参数命名，在Mybatis的mapper中加上该注解，传递的参数与Sql中的字段名一致。

```text
List<Employee> getAllEmployeeByPage(@Param("page") Integer page, @Param("size") Integer size);
```

### 二、@RequestParam

一般用在Controller层，用来解决前端与后端参数不一致的问题，在参数上加上@RequestParam，那么前端的参数必须和后端参数一致，否则会报错。

当只有一个参数的时候，Controller层中@RequestParam和@Param可以互用，当有多个参数的时候，Controller层中@RequestParam和@Param不能互用

```text
@GetMapping("/")
public RespPageBean getAllEmployeeByPage(@RequestParam(defaultValue = "1")Integer page,@RequestParam(defaultValue = "10")Integer size){
    return salaryService.getAllEmployeeByPage(page,size);
}
```

### 二、两者的区别
