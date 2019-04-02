# MySqlStudy
从这里开始学习MySql

## 1.1 - MySQL 软件安装及数据库基础

## 1.2 - MySQL 基础 （一）查询语句

以上基本就是参考[http://www.runoob.com/mysql/mysql-install.html]

### 项目一：查找重复的电子邮箱（难度：简单）
创建 email 表，并插入如下三行数据
```
+----+---------+
| Id | Email   |
+----+---------+
| 1  | a@b.com |
| 2  | c@d.com |
| 3  | a@b.com |
+----+---------+
```
编写一个 SQL 查询，查找 email 表中所有重复的电子邮箱。
根据以上输入你的查询应返回以下结果：
```
+---------+
| Email   |
+---------+
| a@b.com |
+---------+
```
说明：所有电子邮箱都是小写字母。

#### 解题：
```
-- 创建表
CREATE TABLE email (
ID INT NOT NULL PRIMARY KEY,
Email VARCHAR(255) NOT NULL
);()

-- 插入数据
INSERT INTO email VALUES('1','a@b.com');
INSERT INTO email VALUES('2','a@b.com');
INSERT INTO email VALUES('3','a@b.com');
```

查找 email 表中所有重复的电子邮箱
```
select Email from email GROUP BY Email HAVING count(Email) > 1;
```

### 项目二：查找大国（难度：简单）
创建如下 World 表
```
+------------+----------+---------+--------------+---------------+
| name       | continent| area    | population   | gdp           |
+------------+----------+---------+--------------+---------------+
| Afghanistan| Asia     | 652230  | 25500100     | 20343000      |
| Albania    | Europe   | 28748   | 2831741      | 12960000      |
| Algeria    | Africa   | 2381741 | 37100000     | 188681000     |
| Andorra    | Europe   | 468     | 78115        | 3712000       |
| Angola     | Africa   | 1246700 | 20609294     | 100990000     |
+------------+----------+---------+--------------+---------------+
```
如果一个国家的面积超过 300 万平方公里，或者(人口超过 2500 万并且 gdp 超过 2000 万)，那么这个国家就是大国家。
编写一个 SQL 查询，输出表中所有大国家的名称、人口和面积。
例如，根据上表，我们应该输出:
```
+--------------+-------------+--------------+
| name         | population  | area         |
+--------------+-------------+--------------+
| Afghanistan  | 25500100    | 652230       |
| Algeria      | 37100000    | 2381741      |
+--------------+-------------+--------------+
```
#### 解题：
```
-- 创建表
CREATE TABLE World (
name VARCHAR(50) NOT NULL,
continent VARCHAR(50) NOT NULL,
area INT NOT NULL,
population INT NOT NULL,
gdp INT NOT NULL
);
-- 插入数据
INSERT INTO World
  VALUES('Afghanistan','Asia',652230,25500100,20343000);
INSERT INTO World 
  VALUES('Albania','Europe',28748,2831741,12960000);
INSERT INTO World 
  VALUES('Algeria','Africa',2381741,37100000,188681000);
INSERT INTO World
  VALUES('Andorra','Europe',468,78115,3712000);
INSERT INTO World
  VALUES('Angola','Africa',1246700,20609294,100990000);
```
输出表中所有大国家的名称、人口和面积。
```
SELECT name,population,area FROM world WHERE area > 3000000 or (population > 25000000 and gdp > 20000000);
```
