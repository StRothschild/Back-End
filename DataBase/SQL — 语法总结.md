## SQL 语法总计
#### LEFT JOIN ... ON ...
##### LEFT JOIN 关键字会从右表那里返回所有的行并合入左表中
```SQL
SELECT *
FROM RightTable r
LEFT JOIN LeftTable l ON r.Id = l.Id;
```



#### UNION
##### UNION 会合并两个或多个 SELECT 语句的结果集，但要求 SELECT 返回相同的列的数量
```SQL
SELECT id, name
FROM firstTable
UNION
SELECT id, name
FROM secondTable
```


#### LEFT JOIN ... ON ... 与 UNION 的区别
##### 两者都有合并表的功能
##### LEFT JOIN ... ON ... 是在水平方向上的多表合并，UNION 的合并是在垂直方向上的多表合并





---
#### GROUP BY
##### GROUP BY 会将某一相同字段的所有记录合并成一条记录
```SQL
SELECT *
FROM A a
GROUP BY a.Id;
```



---
#### DISTINCT & GROUP BY
##### DISTINCT 和 GROUP BY 一样有去重的效果。但相比之下 GROUP BY 的效率更高，一般使用 GROUP BY。
