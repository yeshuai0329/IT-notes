### MongoDB 简介和命令

#### 一、MongoDB 简介

**一、MongoDB是什么？**

> MongoDB 是一个基于分布式文件存储的数据库。由 C++ 语言编写。旨在为 WEB 应用提供可扩展的高性能数据存储解决方案。
>
> MongoDB 是一个介于  **关系型数据库**  和  **非关系型数据库**  之间的产品，是非关系型数据库当中功能最丰富，最像关系型数据库的。
>
> MongoDB 将数据存储为一个文档，数据结构由键值(key=>value)对组成。MongoDB 文档类似于 JSON 对象。字段值可以包含其他文档，数组及文档数组。

```json
{
  "name":"sue",											          		-----field:value
  "age":26,												                -----field:value
  status:"A",										              		-----field:value
  groups:["news","sports"]												-----field:value
}
```



#### **二、关系型数据库与非关系型数据库**

> 关系型数据库又称：RDBMS

> 非关系型数据库又称：NoSQL

**1. 两者的代表**

1. 关系型数据库：Oracle、Microsoft SQL Server、MySQL
2. 非关系型数据库：Redis、MongodDB、Neo4j、Hbase



**2. 两者的区别RDBMS**

- 高度组织化结构化数据（二维表）
- 结构化查询语言（SQL）
- 数据和关系都存储在二维表中
- 数据操纵语言，数据定义语言
- 严格的一致性
- 事务

NoSQL

- 代表着不仅仅是SQL
- 没有声明性查询语言
- 没有预定义的模式
- 键值对存储，列存储，文档存储
- 非结构化数据
- 高性能，高可用性和可伸缩性

#### 三、MongoDB 历史

- 2007年10月，MongoDB由10gen团队所发展。2009年2月首度推出。
- 2012年05月23日，MongoDB2.1 开发分支发布了! 该版本采用全新架构，包含诸多增强。
- 2012年06月06日，MongoDB 2.0.6 发布，分布式文档数据库。
- 2013年04月23日，MongoDB 2.4.3 发布，此版本包括了一些性能优化，功能增强以及bug修复。
- 2013年08月20日，MongoDB 2.4.6 发布。
- 2013年11月01日，MongoDB 2.4.8 发布。
- ......

#### 四、MongoDB 术语/概念

| SQL术语/概念 | MongoDB术语/概念 |             解释/说明             |
| :----------: | :--------------: | :-------------------------------: |
|   database   |     database     |              数据库               |
|    table     |    collection    |           数据库表/集合           |
|     row      |     document     |          数据记录行/文档          |
|    column    |      field       |            数据列/字段            |
|    index     |      index       |               索引                |
| table joins  |                  |       表连接。MongoDB不支持       |
| primary key  |   primary key    | 主键。 MongoDB使用 _id 字段为主键 |

#### 五、MongoDB 命令

##### 一、数据库常用命令与方法

1. ###### 查看所有的数据库

```bash
 $ show dbs
```

**注意：当某个数据库下没有数据时是 show 不出来的。**



2. ###### 创建/切换数据库

```bash
$ use <数据库名>
```

**注意：要切换的数据库不存在时，会先创建出来再切换过去。**



3. ###### 查看当前使用的数据库

```bash
$ db

$ db.getName()
```

**注意：默认都会是 test** 



###### 4. 显示当前数据库状态

```bash
$ db.stats()
```



###### 5. 删除当前数据库

```
$ db.dropDatabase()
```

**注意：通过 show dbs 查看是否还在**



##### 二、集合（collection）常用命令与方法

###### 1. 创建集合

```bash
$ db.createCollection('集合名字')
```



###### 2. 查看当前数据库下所有的集合

```bash
$ db.getCollectionNames()

$ show collections
```



###### 3. 删除集合

```bash
$ db.集合名.drop()
```



##### 三、文档（document）常用命令与方法

###### 1. 添加

- save

```bash
bash$ db.<集合名>.save( document )
```

- insert

```bash
$ db.<集合名>.insert( docuemnt || [...document] )
```

- insertOne

```bash
$ db.<集合名>.insertOne( document )
```

- insertMany



```bash
$ db.<集合名>.insertMany([...document])
```



###### 2. 修改

- save   

**注意：传入 _id 时，可实现修改,可以理解为直接覆盖之前的 document**

```bash
$ db.<集合名>.save( document )
```



- update

```bash
$ db.<集合名>.update(
    <query>,
  <update>,
  <options>
}
```

- - query：查询条件
  - update：修改内容 ！！！
  - options：一些额外选项配置

- - - upsert：如果查询不到的时候是否直接增加这条记录。默认是 false 
    - multi：是否更新多条，默认是 false



- updateOne
- updateMany



###### 3. 删除

- remove

```
$ db.<集合名>.remove(
    <query>,
  <options>
)
```

- - query：查询条件
  - options：配置项

- - - justOne：是否只删除一条，默认是 false



- deleteOne
- deleteMany



###### 4. 查询

- 查询所有记录

```bash
$ db.hello.find()
```



- 查询 age = 22 的记录

```bash
$ db.hello.find( { age: 22 } )
```



- 查询 age> 22 的记录

```bash
$ db.hello.find( { age: { $gt: 22 } } )
```



- 查询 age < 22 的记录

```bash
$ db.hello.find( { age: { $lt: 22 } } )
```



- 查询 age >= 22 的记录

```bash
$ db.hello.find( { age: { $gte: 22 } } )
```



- 查询 age <= 22 的记录

```bash
$ db.hello.find( { age: { $lte: 22 } } )
```



- 查询 age != 22 的记录

```bash
$ db.hello.find( { age: { $ne: 22 } } )
```



- 查询 age >= 23 并且 age <= 26 的记录

```bash
$ db.hello.find( { age: { $gte: 23, $lte: 26 } } )
```



- 查询 age >= 50 或者 name = 林强 的记录

```bash
$ db.hello.find( { $or: [ { age: { $gte: 50 } }, { name: '林强' } ] } )
```



- 查询 name = 张三 并且 age = 20 的记录

```bash
$ db.hello.find({ name: '张三', age: 20 })
```



- 查询 name 中包含 mongo 的记录

```bash
$ db.hello.find({ name: /mongo/ })
```



- 查询 name 中以 张 开头的记录

```bash
$ db.hello.find({ name: /^张/ })
```



- 查询 name 中以 mongo 结尾的记录

```bash
$ db.hello.find({ name: /mongo$/ })
```



- 查询 指定 name、age 字段的记录

```bash
# _id 会默认有
$ db.hello.find({}, { name: 1, age: 1 })

# 如果不想要 _id
$ db.hello.find({}, { name: 1, age: 1, _id: 0 })

# 如果只是排除掉一个或几个
$ db.hello.find({}, { address: 0 })
```



- 查询 指定 name、age 字段并且 age > 45 的记录

```bash
$ db.hello.find({ age: { $gt: 45 } }, { name: 1, age: 1 })
```



- 查询 按 age 升序的记录

```bash
$ db.hello.find().sort({ age: 1 })
```



- 查询 按 age 倒序的记录

```bash
$ db.hello.find().sort({ age: -1 })
```



- 查询 10 条之后的记录。（跳过前10条）

```bash
$ db.hello.find().skip(10)
```



- 查询 5 条记录。（限制条数）

```bash
$ db.hello.find().limit(5)
```



- 查询 10 条之后的 5 条记录

```bash
$ db.hello.find().skip(10).limit(5)
```



- 查询 第一条 记录

```bash
$ db.hello.findOne()
```



- 获取查询结果的个数

```bash
$ db.hello.find().count()
```