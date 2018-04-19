## MyBatis 语法总结

- #### # 与 $ 的区别
  ##### # 会将传入的变量变成字符串（加单引号），可以防止 SQL 注入攻击
  ##### $ 会直接传入的变量
  ```SQL
  /* # 会添加单引号 */
  假设 bar = test
  select * from foo where bar = #bar#;   =>  select * from foo where bar = 'test';

  /* $ 会直接引用变量的值 */
  假设 foo = test
  select * from $foo$;   =>  select * from test; （注意此处只能用 $, 如果用 # 会引入单引号造成语法错误）
  ```




- #### 常见错误汇总
  ```XML
  提示： You have an error in your SQL syntax; check the manual
        that corresponds to your MySQL server version for the
        right syntax to use near
  原因： 在提示的错误语句之前有漏逗号。
  ```
