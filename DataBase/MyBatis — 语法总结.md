## MyBatis 语法总结

- #### # 与 $ 的区别
  ##### # 最终会将传入的变量变成字符串（加单引号），可以防止 SQL 注入攻击
  ##### $ 会将传入的变量直接替换进 SQL
  ```SQL
  /* # 会添加单引号 */
  假设 bar = test
  select * from foo where bar = #bar#;   =>  select * from foo where bar = 'test';

  /* $ 会直接引用变量的值 */
  假设 foo = test
  select * $foo$;   =>  select * from test; （注意此处只能用 $, 如果用 # 会引入单引号造成语法错误）
  ```
