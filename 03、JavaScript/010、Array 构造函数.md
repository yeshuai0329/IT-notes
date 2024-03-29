#### 一、数组的常用方法

#####   1.1.增

- **`数组.unshift(item)`;** **从数组前面增加一个元素**
  - 作用:从数组前面增加一个元素
  - 参数:item要新增的那个元素
  - 返回值:数组的长度
  - 注意点:直接在原数组操作
- **`数组.push(item)`**：**从数组后面增加一个元素**
  - 作用:从数组后面增加一个元素
  - 参数:item要新增的那个元素
  - 返回值:数组的长度
  - 注意点:直接在原数组操作

##### 1.2.删

* **`数组.shift()`**：**删除数组中的第一个元素**

  * 作用：删除数组中的第一个元素。
  * 返回值：被删除的那个元素。 
  * 参数：无
  * 注意：直接在原数组操作，不会生成新数组。

* **`数组.pop()`**：**删除数组中的最后一个元素**

  * 作用：删除数组中的最后一个元素
  * 返回值：被删除的那个元素。
  * 参数：无
  * 注意：直接在原数组操作，不会生成新数组。

* **`数组.splice(start,n)`**：** **从数组的start位置开始删除n个元素**

  * 作用:从数组的start位置开始删除n个元素
  * 参数:start表示从哪个索引开始删除,n表示要删除几个元素
  * 返回值:被删除的元素的集合
  * 注意点:直接在原数组操作

  **`数组.splice(start,n,.....)`**：**从数组的start位置开始删除n个元素，然后再添加什么元素**

  * 作用:从数组的start位置开始删除n个元素,新增m个元素
  * 参数:start表示从哪个索引开始删除或者增加,n表示要删除几个元素,后面由m个参数,就是要增加要数组中的新元素,从索引是start位置开始增加。
  * 返回值:被删除的元素的集合
  * 注意点:直接在原数组操作

##### 1.3.截取

* **`数组.slice(start,end)`：从数组中截取一部分**
  * 作用:从数组中截取一部分
  * 参数:start表示开始截取的索引,end表示结束截取的索引,包start,不包end，（包前不包后）
  * 返回值:返回一个新的数组，包含从 start 到 end （不包括该元素）的 所有元素
  * 注意点:返回一个新数组,原数组不变

##### 1.4.**颠倒数组**

* **`数组.reverse()`**：**颠倒数组**
  * 作用:颠倒数组
  * 参数:无
  * 返回值:原数组
  * 注意点:直接在原数组操作

##### 1.5.**连接数组**

* **`数组1.concat(数组2,数组3,......)`：**
  * 作用:用于连接多个数组
  * 参数:要被连接的那些数组
  *  返回值:连接好的新数组
  * 注意点:不在原数组操作,会产生新数组

##### 1.6.数组变字符串

* 数组.join("分割符")：把数组变成字符串
  * 作用:把数组变成字符串
  * 参数:默认是逗号,分隔符
  * 返回值:生成的那个字符串
  * 注意点:不会改变原数组

##### 1.7.查询

* **数组.indexof(ele,start)**

  * 作用：查找数组中某个元素的索引

  * 返回值：如果没找到就返回-1，如果找到了就返回该元素的索引值。

  * 参数：第一个参数ele是：要查找的那个元素

      ​    第二个参数start：从哪里开始查找，默认从零开始找

* **数组.lastIndexof(ele,start)**

  * 作用：查找数组中某个元素的索引

  * 返回值：如果没找到就返回-1，如果找到了就返回该元素的索引值。

  * 参数：第一个参数ele是：要查找的那个元素

      ​    第二个参数start：从哪里开始查找，默认从零开始找

##### 1.8.数组排序

* **`数组.sort(fn)`**;

  * 作用:按照指定规则进行排序

  * 参数:如果不写参数,默认是按照字符编码的顺序进行排序,如果写参数,参数fn是表示排序  规则的函数

  * 返回值:返回值就是拍好序的数组

  * 注意点:直接在原数组操作

  * 有参数:参数是表示排序规则的函数

  * 示例“

    ```javascript
    arr.sort(function(a,b){
    
      return a-b;
    
    })由小到大排序
    
    arr.sort(function(a,b){
    
      return b-a;
    
    })由大到小排序
    ```

#### 二、数组的遍历

##### 1.for循环

```javascript
for(var i=0;i<arr.length;i++){
    console.log(arr[i])
}

```

##### 2.for in 循环

```javascript
for( var index in arr){
//固定写法,arr是要循环的数组,index是循环到的那个元素的索引
console.log("当前循环到的是第"+index+'个元素,元素的值是:'+arr[index])
}
```

##### 3.forEach()循环

```javascript
数组.forEach(function(value,index){
    要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    console.log("当前循环到的是第"+index+'个元素,元素的值是:'+value)
})
//参数:要循环执行的函数,函数有两个形参,第一个形参实循环到的那个数组元素的值,第二个形参实循环到的那个数组元素的索引
//注意点:不会改变原数组
```

##### 4.map()循环

```javascript
数组.map(function(value,index){
    要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    return value-1
})
//作用:循环数组
//参数:要循环执行的函数,函数有两个形参,第一个形参实循环到的那个数组元素的值,第二个形参实循环到的那个数组元素的索引
//返回值:整个map的返回值是每一次循环的函数的返回值的集合
//示例：
var arr = [23,45,43,78,23,12,46,28,97];
console.log(arr)
var newArr = arr.map(function(value,index){
    return value-1;
})
console.log(newArr)//newArr = [22,44,42,77,22,11,45,27,96]
```

##### 5.fliter()循环

```javascript
数组.fliter(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
    //符合条件的返回true
    //不符合条件的返回false
   if(value>40){
       return true
   }else{
       return false
   }
})
//作用：过滤数组中符合条件的元素，返回值是新的数组
```

##### 6.every()循环

```javascript
数组.every(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
})
//作用：判断数组中的每一个元素是否都符合条件，符合返回值true，不符合返回值false
//示例：
var arr = [1,15,26,48,45,25,14,44]
var res = arr.every(function(value,index){
    return value>30;
})
console.log(res)
```

##### 7.some()循环

```javascript
数组.some(function(value,index){
    //要循环执行的函数，数组里面有多少个元素，该函数就执行多少次
})
//作用：判断数组中的每一个元素是否有符合条件，符合返回值true，不符合返回值false
//示例：
var arr = [1,15,26,48,45,25,14,44]
var res = arr.every(function(value,index){
    return value>30;
})
console.log(res)
```

