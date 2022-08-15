# moment 高频使用方法

### 1、获取当前moment对象

```javascript
const nowTime = moment() // 返回的是moment时间对象
```

### 2、获取时间戳

```javascript
# 精确到毫秒
// 输出自 Unix 纪元以来的毫秒数
moment().valueOf()
// 输出自 Unix 纪元以来的毫秒数的字符串
moment().format('x')

# 精确到秒
// 输出自 Unix 纪元以来的秒数
moment().unix()
// 输出自 Unix 纪元以来的秒数的字符串
moment().format('X')
```

### 3、生成指定时间的moment

```javascript
moment("1995-12-25");
 
# 带格式
# 解析器会忽略非字母和数字的字符，因此以下两个都将会返回相同的东西。
moment("12-25-1995", "MM-DD-YYYY");
moment("12/25/1995", "MM-DD-YYYY");
```

### 4、返回对象

```javascript
moment().toObject();
# 返回一个包括：年、月、日、时、分、秒、毫秒的对象
{
    years: 2020
    months: 2
    date: 14
    hours: 18
    minutes: 47
    seconds: 56
    milliseconds: 526
}
```

### 5、format格式化

```javascript
moment().format(); // '2021-10-11T12:25:44+08:00'
moment().format('YYYY-MM-DD HH:mm:ss'); // '2020-03-14 19:23:29'
```

### 6、获取时间

```javascript
// 获取今天0时0分0秒
moment().startOf('day')
 
// 获取本周第一天(周日)0时0分0秒
moment().startOf('week')
 
// 获取本周周一0时0分0秒
moment().startOf('isoWeek')
 
// 获取当前月第一天0时0分0秒
moment().startOf('month')
 
// 获取指定日期的0时0分0秒
moment('2019-10-20').startOf('day')
 
// 获取今天23时59分59秒
moment().endOf('day')
 
// 获取本周最后一天(周六)23时59分59秒
moment().endOf('week')
 
// 获取本周周日23时59分59秒
moment().endOf('isoWeek')
 
// 获取当前月最后一天23时59分59秒
moment().endOf('month')

// 获取当地时间
moment().format() // '2021-10-11T14:20:11+08:00'

// 获取国际标准时间
moment().utc().format() // '2021-10-11T06:20:00Z'

// 国际时间转当前时间
moment('2021-10-11T06:20:00Z').format() // '2021-10-11T14:20:11+08:00'

// 当前时间转国际时间
moment('2021-10-11T14:20:00+08:00').utc().format() // '2021-10-11T06:20:00Z'
```

### 7、获取当月第一天是星期几

```javascript
// 用于获取星期几，其中星期日为 0、星期六为 6
moment().startOf('month').day() 
```

### 8、获取前n天 / 后n天

```javascript
// 获取当前前n天 / 后n天
moment().add(7, 'days');
moment().subtract(7, 'days')
// 获取指定时间前n天 / 后n天
moment('2021-12-25').add(7, 'days');
moment('2021-12-25').subtract(7, 'days')
```

### 9、比较两个时间的大小

```javascript
// 第二个参数用于确定精度，且不仅仅是要检查的单个值，因此使用 day 将会检查年份、月份、日期。
moment('2010-10-31').isBefore('2010-12-31', 'day'); // true
moment('2010-10-20').isBefore('2010-12-31', 'year'); // false
moment('2010-10-20').isAfter('2009-12-31', 'year'); // true
# 判断两个时间是否相等
moment('2010-10-20').isSame('2009-12-31', 'year'); 
# 需要注意的是， isBefore与isAfter 都是开区间，如果想使用闭区间，应使用
isSameOrBefore
isSameOrAfter
```

### 10、计算两个时间相差几天

```javascript
moment([2008, 2, 27]).diff([2007, 0, 28], 'day'); // 424
moment('2021-12-22').diff('2015-12-22', 'day'); // 2192
```

### 11、获取当月总天数

```javascript
// 获取当月天数
moment().daysInMonth()
// 获取指定月份的天数
moment('2021-9').daysInMonth()
```

### 12、判断一个日期是否在两个日期之间

```javascript
// 两遍开区间
moment('2010-10-20').isBetween('2010-10-19', '2010-10-25') // true
moment('2010-10-19').isBetween('2010-10-19', '2010-10-25'); // false
moment('2010-10-25').isBetween('2010-10-19', '2010-10-25'); // false
// 第四个参数控制开闭区间
moment('2016-10-30').isBetween('2016-10-30', '2016-12-30', null, '()'); //false
moment('2016-10-30').isBetween('2016-10-30', '2016-12-30', null, '[)'); //true
moment('2016-10-30').isBetween('2016-01-01', '2016-10-30', null, '()'); //false
moment('2016-10-30').isBetween('2016-01-01', '2016-10-30', null, '(]'); //true
moment('2016-10-30').isBetween('2016-10-30', '2016-10-30', null, '[]'); //true
```

### 13、判断时间是多久以前

```javascript
moment().fromNow() // 几秒前
moment([2007, 0, 29]).fromNow() //15年前
```

下表概述了每个时间长度显示的字符串的细分。

| 范围                   | 键   | 样本输出               |
| :--------------------- | :--- | :--------------------- |
| 0 至 44 秒             | s    | 几秒前                 |
| *未设定*               | ss   | 44 秒前                |
| 45 至 89 秒            | m    | 1 分钟前               |
| 90 秒至 44 分钟        | mm   | 2 分钟前 ... 44 分钟前 |
| 45 至 89 分钟          | h    | 1 小时前               |
| 90 分钟至 21 小时      | hh   | 2 小时前 ... 21 小时前 |
| 22 至 35 小时          | d    | 1 天前                 |
| 36 小时至 25 天        | dd   | 2 天前 ... 25 天前     |
| 26 至 45 天            | M    | 1 个月前               |
| 45 至 319 天           | MM   | 2 个月前 ... 10 个月前 |
| 320 至 547 天 (1.5 年) | y    | 1 年前                 |
| 548 天+                | yy   | 2 年前 ... 20 年前     |

### 更多使用方法请上 [moment ](http://momentjs.cn/) 官网查看

