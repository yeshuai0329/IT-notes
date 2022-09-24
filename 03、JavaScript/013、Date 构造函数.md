> Date构造函数，创建一个实例，保存的现在的时间对象。

### 1. `new Date()`

- 参数： 

  ```javascript
  new Date();
  //如果没有提供参数，那么新创建的Date对象表示实例化时刻的日期和时间。
  new Date(value);  
  //一个 Unix 时间戳（Unix Time Stamp），它是一个整数值，表示自1970年1月1日00:00:00 UTC（the Unix epoch）以来的毫秒数，忽略了闰秒。请注意大多数 Unix 时间戳功能仅精确到最接近的秒
  new Date(dateString); 
  //表示日期的字符串值。该字符串应该能被 Date.parse() 正确方法识别
  new Date(year, monthIndex [, day [, hours [, minutes [, seconds [, milliseconds]]]]]);
  //当至少提供了年份与月份时，这一形式的 Date() 返回的 Date 对象中的每一个成员都来自下列参数。没有提供的成员将使用最小可能值（对日期为1，其他为0）。
  //参数monthIndex 是从“0”开始计算的，这就意味着一月份为“0”，十二月份为“11”。
  ```

  ​	

### 2. 实例可以调用的方法

#### 2.1. `getDate()`

- 根据当地时间，返回当月的那一天。

```javascript
const time = new Date() 
console.log(time) // Sat Sep 10 2022 23:11:02 GMT+0800 (中国标准时间)
const day = time.getDate()
console.log(day)  // 10
```



#### 2.2. `getDay()`

- **`getDay()`** 方法根据本地时间，返回一个具体日期中一周的第几天，0 表示星期天。
- 返回值： 根据本地时间，返回一个 0 到 6 之间的整数值，代表星期几： 0 代表星期日， 1 代表星期一，2 代表星期二， 依次类推。

```javascript
const time = new Date() 
console.log(time) // Sat Sep 10 2022 23:11:02 GMT+0800 (中国标准时间)
const day = time.getDay()
console.log(day) // 6
```

