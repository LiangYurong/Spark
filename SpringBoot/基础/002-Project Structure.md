### 1. project root directory

src/main/java ：source code

src/main/resources：resources code

src/test/java：test code

### 2. start class 

i usually named it as RunApp.java .

the startup class needs to be on top of other classes . 

### 3. Src/main/java

- annotation：custom annotaton
- aspect：aop
- config：configuration
- constant：constant , enum
  - consist：contant definition
  - enums：enum definition
- controller：access path , Generally does not involve bussiness logic .
- filter : to filter or intercept
- mapper：@Repository or @Mapper
- model
- - entity
  - dto
  - vo
- service：business logic interface
- - intf：存放业务逻辑接口定义
  - impl：interface implementation
- utils: tool class 

### 4. src/main/resources

- mapper : xxxMapper.xml
- sql
- static
  - js
  - css
  - image
- templates
  - xxx.html
  - sideBar
  - bottom
- application.yml
- application-dev.yml
- application-test.yml
- application-prod.yml

### 5.src/test/java

- xxxTest.java

