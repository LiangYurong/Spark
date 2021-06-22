


### Json是什么？

把一串JSON转换成Java的对象模型，以及把Java的对象模型转换成一串JSON。

使用key-value形式存储。key必须是String，value可以是其他形式。

### 为什么我们要使用Json？

方便前后端交互。

## FastJson

FastJson为什么这么快？
- 自行编写类似StringBuilder的工具类SerializeWriter。
- 使用ThreadLocal来缓存buf。
- 使用asm避免反射
- 集成jdk实现的一些优化算法

### FastJson基础

JSONObject是 fastJson提供的对象。

想通过键值对的形式获取数据，使用JSONObject。

如果后台查询的是某个bean的list集合向前端页面传递，使用JSONArray。

JSONArray getJSONArray(String key) 

如果JSONObject对象中的value是一个JSONObject数组，既根据key获取对应的JSONObject数组；

toJSONString() /toString()

将JSONObject对象转换为json的字符串

JSONObject.get(String key)

根据key值获取JSONObject对象中对应的value值，获取到的值是Object类型，需要手动转化为需要的数据类型

JSONObject.getString(String key)

获取到的值是String类型


