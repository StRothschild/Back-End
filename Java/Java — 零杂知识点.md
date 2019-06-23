# Java 的零杂知识点

- #### Java 判空
  ```java
  /* 判断是否为空字符串 */
  "".equals(foo)    // "" 写前面可以避免 foo 为 null 时出现的 bug

  /* 判断是否为 null */
  null == foo 或 foo == null  // 建议用前者，万一少写一个等于号时，前者会报错，可以及时发现
  ```

---
- #### 中间件（Middleware）
  ##### 中间件的概念是一种将具体业务和技术实现解耦的组件。通过中间件可以屏蔽底层复杂的技术逻辑（可能由多种技术和服务的聚合来实现），并提供统一的接口来提供特定的服务。
  ##### 数据库中间件作用举例：提供以单表操作的方式来实现底层的多库多表分布式数据系统操作的服务。
  ##### 消息中间件作用举例: 通过提供创建、发送、接收消息的一套方法，实现可靠的、高效的、实时的跨平台数据传输。
  
  
  
---
- #### FastJSON
  ##### JSONObject.parse() 与 JSONObject.parseObject() 不同。前者返回 Object 对象，后者返回一个 JSONObject 对象。
  
  

---
- #### swicth
   ##### switch 支持的变量类型只有 int、short、char、byte 和 enum。
   ##### 对于 enumerate 类型的数据。case 后面不用跟具体类名。
   ```java
   switch(int、short、char、byte、enum){
   case int、short、char、byte、enum:
      // do something
   break;
   ```

---
- #### Java 保留两位小数
    ```java
    // 将 target 保留2位小数
    Double result = (double)Math.round(target * 100)/100
    ```



---
- #### Java 父类强制向下转型
    ```java
    // 当父类无法强制向下转型时，可以用 JSONObject 
    public static void main(String[] args) {
        Father father = new Father();
        String ob = JSONObject.toJSONString(father);
        Son son = JSONObject.parseObject(ob, Son.class);
    }
    ```
    
    

---
- #### Factory
  ##### 工厂方法
    1.简单工厂模式
    2.工厂方法模式：定义一个用于创建对象的接口，让子类决定实例化哪一个类，工厂方法使一个类的实例化延迟到其子类
    3.抽象工厂模式：提供一个创建一系列相关或相互依赖对象的接口，而无需指定它们具体的类。




---
- #### Java8 中的 lambda 表达式
  ##### forEach
    ```java
    // forEach 内的回调函数只能设置 final 类型的变量，或者是 effectivly final 的类型（Java8会在编译时自动加上final）。
    ```
    


---
- #### fastJson
  ##### JSONObject jsonObject = JSON.parseObject(result); 
  
  
  
---
- #### 缩进
  ##### 缩进统一用 4 个空格，不要用 Tab 缩进。应为不同系统和应用的 Tab 缩进距离并不统一，但空格都是一样的。
