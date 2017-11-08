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
- #### Linux 中的数据库操作
  ```
    mysql -h主机地址 -P端口 -u用户名 -p密码     // 连接 MySQL

    exit + 回车                               // 退出 MySQL
  ```
