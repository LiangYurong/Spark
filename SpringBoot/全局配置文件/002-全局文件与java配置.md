### 全局文件 application.properties
```text
wechatpay.MCH_ID = 123
wechatpay.H_APP_ID= 456
```

### java配置类
```java
@Component
@ConfigurationProperties(prefix = "wechatpay")
@Data
public class WechatPayConfig {
    private String MCH_ID;
    private String H_APP_ID;
}
```

### 使用
```text
@AutoWired
private WechatPayConfig wx;

wx.getMCH_ID(); // 使用get获取到某个字段
```

