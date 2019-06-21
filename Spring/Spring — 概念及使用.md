## Spring 的概念及使用

---
- 依赖注入(Dependency Injection)
- 控制反转(Inversion of Control)



---
- #### Spring + IDEA 起步流程
  ##### 1. 下载并安装 Tomcat
  ##### 2. 下载并安装 Maven（可以跳过，IDEA 中内置了 Maven）
  ##### 3. 在 IDEA 中创建一个 Maven 工程（如果创建 web 工程 archeType 可以选择 maven-archetype-webapp，其他类型工程可以选 maven-archetype-quickstart）
  ##### 4. 配置 pom.xml 引入 Spring 及其他相关依赖





---
- #### Spring Bean
  ##### Spring Bean 是被实例化的，被 Spring 容器管理的 Java 对象。
  ##### 1. Bean 配置信息定义了 Bean 的实现及依赖关系。
  ##### 2. Spring 容器根据各种形式的 Bean 配置信息在容器内部建立Bean定义注册表，然后根据注册表加载、实例化 Bean，并建立 Bean 之间的依赖关系。
  ##### 3. 最后将这些准备就绪的Bean 放到 Bean 缓存池中，以供外层的应用程序进行调用。
  
  https://www.cnblogs.com/wuchanming/p/5426746.html



---
-  #### Spring Bean 的三种配置方案
  | XML | 注解 | 代码
  |--|--|--|
  |\<bean> | @Component / @Controller / @Service / @Repository |--|




---
- #### SpringMVC 概念
  ##### SpringMVC 是一个基于 DispatcherServlet 的MVC框架，DispatcherServlet 继承自HttpServlet。每一个 Request 都是由 DispatcherServlet 负责转发给相应的 Handler，Handler处理以后再返回相应的视图(View)和模型(Model)，返回的视图和模型都可以不指定，即可以只返回 Model 或只返回 View 或都不返回。






---
- #### web.xml 中配置 Spring
  ```xml
  <--! 要读入的 spring 配置文件的位置 -->
  <context-param>  
      <param-name>contextConfigLocation</param-name>  
      <param-value>/WEB-INF/spring-config.xml</param-value>  
  </context-param>
  ```
  
  

---
- #### 配置文件中的通配符 *
  ```javascript
  /* 配置文件中的通配符 * 和 ** 代表了不同含义 */

  // 单个 * 只匹配路径下的所有文件，例如 /resources/test.html   但是不会匹配目录
  <mvc:resources mapping="/resources/*" location="/resources/" />

  // 两个 ** 可以同时匹配路径下的所有文件和目录，例如 /resources/folder 和 /resources/test.html
  <mvc:resources mapping="/resources/**" location="/resources/" />
  ```


---
- #### @Autowired
  ##### 如果类是通过 new 方法被实例化，而不是通过 @Autowired 方法被实例化的。那么这个类自身所包含的，通过 @Autowired 注入的类不会被实例化，会是 null。
  
  

---
- #### @schedule
  ##### @Scheduled注解为定时任务，通过 cron 表达式来控制执行的时机
  ```java
  @Scheduled (cron="0/5 * * * * ?")   // 每5秒执行一次 
  @Scheduled (cron="0 0/30 9-17 * * ?")   //朝九晚五工作时间内每半小时
  @Scheduled (cron="0 15 10 ? * MON-FRI")   //周一至周五的上午10:15触发 
      
  * 字符代表所有可能的值
  / 字符用来指定数值的增量 比如 "0/15" 表示从第 0 分钟开始，每 15 分钟
  ? 字符仅被用于天（月）和天（星期），表示不指定值。当其中之一被指定了值以后，为了避免冲突，需要将另一个子表达式的值设为 "?"
  ```

