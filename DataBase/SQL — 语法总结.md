## SQL 语法总结
- #### 转义
  ##### 如果数据库中的字段名和保留字冲突则使用（\`）撇号来进行转义
  ```SQL
  SELECT bar FROM foo;          // 正常 SQL 语句
  SELECT `from` FROM foo;       // from 是 SQL 中的保留字段，需要转义

  SELECT 'from' FROM foo;       // 注意与单引号的区别，此处使用单引号表明是普通字符串，返回结果是 'from'
  ```




---
- #### DEFUALT
  ##### 不加 not null default 都是 default null
  ```SQL
  // a、b 的默认值都是 null， c 的默认值为 'test'
  create table `foo`
  (  
    `a` varchar(255),
    `b` varchar(255) DEFAULT NULL,
    `c` varchar(255) NOT NULL DEFULT 'test'
  ) ENGINE=InnoDB DEFAULT CHARSET=utf8
  ```




---
- #### COUNT
  ##### COUNT(column_name) 函数返回指定列的值的数目，但是不包含 null 值。
  ##### COUNT(*) 与 COUNT(1)包含 null 值。
  ##### 通常情况下 COUNT(*) 会扫描所有列，而 COUNT(1)只扫描第一列，所以一般 COUNT(1) 的效率高。
  ##### 注意 COUNT 在与 GROUP BY 联用时，COUNT 的结果是每一条 GROUP BY 结果内的数据条数，而不是 GROUP BY 后返回的所有结果条数。
  ```SQL
  +-----+-----+
   | id | num
  +-----+-----+
   | 1 | 8 |
   | 1 | 8 |
   | 1 | 8 |
   | 32 | 8 |
   | 32 | 8 |
   | 32 | 8 |
   | 32 | 8 |

   SELECT count(*) FROM table GROUP BY id;

   +------------+
   | count(*) |
   +-----------+
   | 3 |
   | 4 |  
  ```




---
- #### INNER JOIN ... ON ...
  ##### INNER JOIN 可以直接简写成 JOIN
  ##### INNER JOIN 不会以某张表为基准，只要匹配的规则都会被返回。
  ```SQL
  SELECT *
  FROM foo f
  JOIN bar b ON f.Id = b.Id;
  ```


---
- #### LEFT JOIN ... ON ...
  ##### LEFT JOIN 关键字会从右表那里返回和左表相同行数的所有列，并合入左表中。注意，如果某行的 on 条件不符合，则右表返回的值均为 null。
  ##### LEFT JOIN 对性能的消耗较大
  ```SQL
  SELECT *
  FROM RightTable r
  LEFT JOIN LeftTable l ON r.Id = l.Id;
  ```


---
- #### UNION
  ##### UNION 会合并两个或多个 SELECT 语句的结果集，但要求 SELECT 返回相同的列的数量
  ```SQL
  SELECT id, name
  FROM firstTable
  UNION
  SELECT id, name
  FROM secondTable
  ```


---
- #### LEFT JOIN ... ON ... 与 UNION 的区别
  ##### 两者都有合并表的功能
  ##### LEFT JOIN ... ON ... 是在水平方向上的多表合并，UNION 的合并是在垂直方向上的多表合并




---
- #### GROUP BY
  ##### GROUP BY 会将某一相同字段的所有记录合并成一条记录
  ```SQL
  SELECT *
  FROM A a
  GROUP BY a.Id;
  ```



---
- #### DISTINCT & GROUP BY
  ##### DISTINCT 和 GROUP BY 一样有去重的效果。但相比之下 GROUP BY 的效率更高，一般使用 GROUP BY。




---
- #### ORDER BY
  ##### ORDER BY  语句用于对结果集进行排序
  ```SQL
  SELECT *
  FROM A a
  ORDER BY a.Id;
  ```
