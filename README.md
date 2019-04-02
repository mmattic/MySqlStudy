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
