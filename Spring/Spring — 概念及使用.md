## Spring 的概念及使用

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
- #### @schedule
  ##### @Scheduled注解为定时任务，通过 cron 表达式来控制执行的时机
  ```java
  @Scheduled (cron="0/5 * * * * ?")   // 每5秒执行一次 
  @Scheduled (cron=" 0 0/30 9-17 * * ?")   //朝九晚五工作时间内每半小时
     
  * 字符代表所有可能的值
  / 字符用来指定数值的增量 比如 "0/15" 表示从第 0 分钟开始，每 15 分钟
  ? 字符仅被用于天（月）和天（星期），表示不指定值。当其中之一被指定了值以后，为了避免冲突，需要将另一个子表达式的值设为 "?"
  ```

