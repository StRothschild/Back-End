## MySQL 使用总结

- #### Schema
  ##### MySQL 中的 Schema 概念类似于 SQL Server 中的库。在一个 MySQL 容器中，可以有多个 Schema（库）。每个 Schema（库）中可以存在多张表（table）。



---
- #### MySQL 中的大小写
  ##### 1. MySQL 默认不区分大小写。
  ##### 2. 大小写是否敏感可以由配置文件（my.cnf / my.ini）中的 lower_case_table_names 来控制。为 0 时表示区分大小写，为 1 时表示将名字转化为小写后存储，不区分大小写。

  ##### 3. MySQL 在 Linux 下数据库名（Schema）、表名、列名、别名的规则如下：
  ```
  1、数据库名与表名和表的别名 大小写敏感
  2、列名与列的别名在任何情况下 大小写不敏感
  3、字段内容默认情况下 大小写不敏感
  ```



---  
- #### 时间处理语法
  ##### DATE_SUB() 函数用于将时间减去指定的时间间隔
  ##### DATE_FORMAT() 函数用于以不同的格式显示日期/时间数据
  ```SQL
  /* 2018-1-29 16:25:46.635 前两天 */
  DATE_SUB(2018-1-29 16:25:46.635, INTERVAL 2 DAY)
  /* 2018-1-29 16:25:46.635 前3小时 */
  DATE_SUB(2018-1-29 16:25:46.635, INTERVAL 3 HOUR)


  /* 当前时间的 2018-02-27 格式 */
  DATE_FORMAT(now(), '%Y-%m-%d')
  /* 当前时间的 18:48:12 格式 */
  DATE_FORMAT(NOW(), '%H:%i:%s')
  /* 当前时间的 18:48:12.258 格式 */
  DATE_FORMAT(NOW(), '%H:%i:%s.%f')
  ```





---  
- #### IF 函数语法
  ##### MySQL 中的 IF 函数类似于 二元表达式
  ```SQL
  IF(a IS NULL, 0, a) ==> 如果表格式的结果为true，则返回 0，否则返回 a
  ```








---
- #### LENGTH 函数语法
  #####  MySQL 中的 LENGTH 函数相当与 SQL 中的 LEN 函数，用于判断 字段 内容的长度
  ```MySQL
  // 获取 foo 字段的长度
  SELECT LENGTH(foo) FROM bar;                     

  // 获取 foo 字段 并按 foo 字段的长度排序
  SELECT foo FROM bar ORDER BY LENGTH(foo) DESC;
  ```










---
- #### LENGTH 函数语法
  #####  MySQL 中的 LENGTH 函数相当与 SQL 中的 LEN 函数，用于判断 字段 内容的长度
  ```MySQL
  // 获取 foo 字段的长度
  SELECT LENGTH(foo) FROM bar;                     

  // 获取 foo 字段 并按 foo 字段的长度排序
  SELECT foo FROM bar ORDER BY LENGTH(foo) DESC;

  // LENGTH 在识别汉字时会返回 3 个字符, 而 CHAR_LENGTH 不会
  SELECT LENGTH('汉字t');        => 7
  SELECT CHAR_LENGTH('汉字t');   => 3
  ```









---
- #### MySQL 特有的防重复插入
  ```
  /* ON DUPLICATE KEY UPDATE */
  INSERT INTO
  recsys.video_vulgarity_check (id, title, currentTime)
  VALUES ('foo', 'title', now())
  ON DUPLICATE KEY UPDATE
  title = VALUES(title),
  currentTime = VALUES(currentTime);

  /* 如果插入过程中 id/title/currentTime 有一个或多个字段是 Primary Key 或者是 UNIQ。则当执行
  INSERT 操作时出现字段重复，则会改为执行 ON DUPLICATE KEY 之后的语句。
  本例中就是 UPDATE title = VALUES(title),currentTime = VALUES(currentTime); */
  ```




---
- #### Linux 中的数据库操作
  ```
    mysql -h 主机地址 -P 端口 -u 用户名 -p 密码     // 连接 MySQL

    exit + 回车                               // 退出 MySQL
  ```
