### 1、SQL语法

#### 1.1、sql 语句的语法规范(你可以不遵守, 建议你遵守)

- sql 语句里面的关键字大写
- 表名和字段名尽可能使用反引号(键盘 tab 键上面那个按钮 ``)包裹

#### 1.2、sql 语句的语法规则(你必须遵守, 不然报错)

* 当你写一些文本内容的时候, 需要使用 引号 包裹, 表示是一个 字符串

#### 1.3、数据库增删改查

- **增：INSERT关键字**

  - ​	一共两种语法：
    1. INSERT INTO `表名` VALUES(数据1, 数据2, 数据3, ...);
       1. 按照你数据库里面字段的顺序插入的
       2. id 我们可以不写, 直接写 null, 会自动增长
    2. INSERT INTO `表名` (字段1, 字段2, ...) VALUES(数据1, 数据2, ...);
       1. 按照你书写的字段添加
       2. 值添加某些字段的内容, 剩下的稍后完善的时候在做

- **删：DELETE关键字**

  -  DELETE FROM `表名` WHERE 条件
     - 要从哪一个表删除条件为什么的数据

- ##### 改：UPDATE关键字

  -  UPDATE `表` SET 字段=新值 WHERE 条件
  -  UPDATE `表` SET 字段=新值, 字段2=新值 WHERE 条件

- **查：SELECT关键字**

  1. SELECT * FROM `表`
     - 查询这个表里面的所有数据
  2. SELECT * FROM `表` WHERE 条件
     - 根据我们的条件查询数据库里面的数据
  3. SELECT * FROM `表` WHERE 条件1 AND 条件2
     - 根据两个条件来查询, 两个条件必须都满足
  4. SELECT * FROM `表` WHERE 条件1 OR 条件2
     - 根据两个条件来查询, 两个条件满足一个就可以了
  5. SELECT * FROM `表` WHERE 字段 LIKE '%关键字%'
     - 查询数据里面指定字段包含某一个关键字的数据

### 2、MYSQL数据库的固定操作

1. 和数据库进行连接
   *  `$link = mysqli_connect('IP地址', '数据库用户名', '数据库密码', '仓库名字');`
2. 设置字符编码
   - `mysqli_set_charset(utf8");`
3. 执行操作
   * `$res=mysqli_query('连接数据库的信息', '你要执行的 sql 语句');`
4. 解析结果
   * `$rows=mysqli_fetch_all($res,1)`
5. 断开数据库连接
   * `mysqli_close($link)`