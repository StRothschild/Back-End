## SQL 语法总计
#### LEFT JOIN ... ON ...
##### LEFT JOIN 关键字会从右表那里返回所有的行并合入左表中。
```SQL
SELECT *
FROM RightTable r
LEFT JOIN LeftTable l ON r.Id = l.Id;
```



---
#### GROUP BY
##### GROUP BY 会将某一相同字段的所有记录合并成一条记录。
```SQL
SELECT *
FROM A a
GROUP BY a.Id;
```



---
#### DISTINCT & GROUP BY
##### DISTINCT 和 GROUP BY 一样有去重的效果。但相比之下 GROUP BY 的效率更高，一般使用 GROUP BY。
