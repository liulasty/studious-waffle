在 SQL 中，连接（JOIN）是用于合并两个或多个表中的数据的关键操作。主要有三种类型的连接：内连接（INNER JOIN）、外连接（OUTER JOIN）和交叉连接（CROSS JOIN）。它们之间的区别在于如何处理连接条件不满足的行。

1. **内连接（INNER JOIN）**：
   内连接返回两个表中满足连接条件的匹配行。语法如下：
   ```sql
   SELECT 列名
   FROM 表1
   INNER JOIN 表2 ON 表1.列 = 表2.列;
   ```
   内连接只返回符合连接条件的行，如果某一行在一个表中没有匹配，则不会包含在结果中。

1. **外连接（OUTER JOIN）**：
   外连接包括左外连接（LEFT OUTER JOIN）、右外连接（RIGHT OUTER JOIN）和全外连接（FULL OUTER JOIN）。
   - 左外连接（LEFT OUTER JOIN）返回左表中的所有行以及右表中满足连接条件的行。如果右表中没有匹配的行，则以 NULL 值填充右表的列。
      基本概念：左外连接返回左表（放在 JOIN 关键字前面的表）的所有记录，以及与右表（JOIN 关键字后面的表）匹配的记录。如果右表中没有匹配的记录，则结果是 NULL。
      ```sql
      SELECT column_name(s)
      FROM table1
      LEFT JOIN table2
      ON table1.column = table2.column;
      
      ```
假设有两个表 boys 和 girls，共享一个公共列 id。左外连接会返回 boys 表的所有记录，即使 girls 表中没有与之匹配的 id，对于那些没有匹配的 boys 记录，girls 列的值将是 NULL。

   - 右外连接（RIGHT OUTER JOIN）返回右表中的所有行以及左表中满足连接条件的行。如果左表中没有匹配的行，则以 NULL 值填充左表的列。
     基本概念：右外连接与左外连接相反，返回右表的所有记录，以及与左表匹配的记录。如果左表中没有匹配的记录，则结果是 NULL。
     ```sql
     SELECT column_name(s)
     FROM table1
     RIGHT JOIN table2
     ON table1.column = table2.column;
     
     ```

   - 全外连接（FULL OUTER JOIN）返回左右两个表中的所有行，如果其中一个表中没有匹配的行，则以 NULL 值填充另一个表的列。
   
   语法如下：
   ```sql
   SELECT 列名
   FROM 表1
   LEFT/RIGHT/FULL OUTER JOIN 表2 ON 表1.列 = 表2.列;
   ```
   
3. **交叉连接（CROSS JOIN）**：
   交叉连接返回两个表的笛卡尔积，即第一个表的每一行与第二个表的每一行进行组合。语法如下：
   ```sql
   SELECT 列名
   FROM 表1
   CROSS JOIN 表2;
   ```
   交叉连接没有连接条件，返回的结果是两个表中的所有可能组合。通常不建议在大型表上使用交叉连接，因为它会产生非常大的结果集。

这些是 SQL 中连接的主要类型及其语法和区别。根据需要选择合适的连接类型以满足查询需求。