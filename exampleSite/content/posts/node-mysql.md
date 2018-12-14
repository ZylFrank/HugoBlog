---
author: "zhangyunlong"
date: 2018-12-14
linktitle: Node Mysql CURD
title: 使用Node操作Mysql
categories: [ "Development", "Node" ]
tags: ["Node", "Mysql"]
description: "该篇内容分两部分，一部分是 Mysql的基本操作；另一部分是 使用Node操作Mysql"
weight: 10
---

### 该篇内容分两部分，一部分是 Mysql的基本操作；另一部分是 使用Node操作Mysql。

相关链接：

[node操作mysql](http://www.runoob.com/nodejs/nodejs-mysql.html)、
[mysql操作](http://www.mysqltutorial.org)、
[语雀链接](https://www.yuque.com/weshow/expand/rmnkbk)

## 开始前的准备

1.Node安装Mysql环境

```shell
npm install mysql
```

2.Node连接Mysql数据库

```javascript
const mysql = require('mysql')
const db = mysql.createConnection({
    host:    localhost
    user:    root
    password:    root
    port:    3306
    database:    test    // 连接已有数据库使用；
});
db.connect((err)=>{
    if(err)    throw err
    console.log('Mysql Connected...');
});
```
3.创建数据库

```shell
CREATE DATABASE test
```
```javascript
db.query('CREATE DATABASE test', (err, result)=>{
    if (err)    throw err;
    console.log(result);
})
```

4.创建表
```
CREATE TABLE IF NOT EXISTS tasks (
    task_id INT AUTO_INCREMENT,
    title VARCHAR(255) NOT NULL,
    start_date DATE,
    due_date DATE,
    status TINYINT NOT NULL,
    priority TINYINT NOT NULL,
    description TEXT,
    PRIMARY KEY (task_id)
)
```
```
consnt sql = 'CREATE TABLE IF NOT EXISTS user(user_id INT AUTO_INCREMENT, user_name VARCHAR(255), title VARCHAR(255), age INT, PRIMARY KEY (user_id))'
db.query(sql, (err, result) => {
    if (err)     throw err;
    console.log(result);
})
```
### CURD操作

1.添加数据
```shell
INSERT INTO table(c1,c2,...)
VALUES
   (v11,v12,...),
   (v21,v22,...),
    ...
   (vnn,vn2,...);
```
```js
  const sql = 'INSERT INTO user(user_name, title, age) VALUES(?,?,?)';
  db.query(sql, [user_name, title, age], (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send('success add user');
  })
```
2.更新数据
```shell
UPDATE [LOW_PRIORITY] [IGNORE] table_name
SET
    column_name1 = expr1,
    column_name2 = expr2,
    ...
WHERE
    condition;
```
```js
  const sql = `UPDATE user SET user_name = ?, age = ?, title = ? WHERE user_id = ${user_id}`;
  db.query(sql, [user_name, age, title], (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send('update success')
  })
```

3.查询数据
```shell
SELECT
    column_1, column_2, ...
FROM
    table_1
[INNER | LEFT |RIGHT] JOIN table_2 ON conditions
WHERE
    conditions
GROUP BY column_1
HAVING group_conditions
ORDER BY column_1
LIMIT offset, length;
```
```js
  const sql = 'SELECT * FROM user';
  db.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send(result);
  })
```
4.删除数据
```shell
DELETE FROM table_name
WHERE condition;
```
```js
  const sql = `DELETE FROM user WHERE user_id = ${user_id}`;
  db.query(sql, (err, result) => {
    if (err) throw err;
    console.log(result);
    res.send('deleted success user');
  })
```
