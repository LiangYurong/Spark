### swagger依赖

```text
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger2</artifactId>
    <version>3.0.0</version>
</dependency>
<dependency>
    <groupId>io.springfox</groupId>
    <artifactId>springfox-swagger-ui</artifactId>
    <version>3.0.0</version>
</dependency>

```

### swagger配置类

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.condition.ConditionalOnProperty;
import org.springframework.context.ApplicationContext;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import com.zteict.rhin.base.commons.utils.SpringUtil;
import org.springframework.web.servlet.config.annotation.ResourceHandlerRegistry;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurationSupport;
import springfox.documentation.builders.ApiInfoBuilder;
import springfox.documentation.builders.PathSelectors;
import springfox.documentation.builders.RequestHandlerSelectors;
import springfox.documentation.service.Contact;
import springfox.documentation.spi.DocumentationType;
import springfox.documentation.spring.web.plugins.Docket;
import springfox.documentation.swagger2.annotations.EnableSwagger2;

/**
 *  swagger配置类
 *  @ConditionalOnProperty：核心功能是通过属性name以及havingValue来实现的。
 *  	1. 默认情况下matchIfMissing为false
 *      2. name用来从application.properties中读取某个属性值
 *  	3. 在matchIfMissing为false时，如果name值为空，则返回false；如果name不为空，则将该值与havingValue指定的值进行比较，如果一样则返回true，否则返回false。返回false也就意味着自动配置不会生效。
 */
@EnableSwagger2
@Configuration
@ConditionalOnProperty(name = "swagger.enable", havingValue = "true")
public class SwaggerConfig extends WebMvcConfigurationSupport {

	/**
	 * 添加摘要信息
	 */
	@Bean
	public Docket controllerApi() {
		return new Docket(DocumentationType.SWAGGER_2)
				.apiInfo(new ApiInfoBuilder().title("专病科研平台")
						.description("描述：专病科研平台,具体包括基于openEHR的CRF表单制作，病例数据关联CRF表单及数据录入，CRF表单数据导出等")
						.contact(new Contact("人口信息平台团队", null, null)).version("1.0").build())
				.select() // select()函数返回一个ApiSelectorBuilder实例,用来控制接口被swagger做成文档
				.apis(RequestHandlerSelectors.basePackage("com.zteict.rhin")) // 用于指定扫描哪个包下的接口
				.paths(PathSelectors.any()) // 选择所有的API,如果你想只为部分API生成文档，可以配置这里
				.build();
	}

	@Override
	protected void addResourceHandlers(ResourceHandlerRegistry registry) {
		// 解决静态资源无法访问
		registry.addResourceHandler("/**").addResourceLocations("classpath:/static/");
		// 解决swagger无法访问
		registry.addResourceHandler("/swagger-ui.html").addResourceLocations("classpath:/META-INF/resources/");
		// 解决swagger的js文件无法访问
		registry.addResourceHandler("/webjars/**").addResourceLocations("classpath:/META-INF/resources/webjars/");
	}

}

```

### 访问swagger文档

启动springboot项目，浏览器输入：http://localhost:8090/swagger-ui.html#/
- 如果访问不到，看全局配置文件application.properties是否添加了访问前缀

端口需要根据项目调整.
