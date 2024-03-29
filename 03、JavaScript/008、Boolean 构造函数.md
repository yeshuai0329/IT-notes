#### 一、字符串的常用方法

1. `indexOf(s1,[s2])`

   - 返回字符串中检索指定字符第一次出现的位置，没找到就返回-1.
   - s1 ： 要查找的字符串（必填）
   - s2 ： 从哪个索引开始查找 （选填）

   ```javascript
   const str = 'abcabcddd'
   str.indexOf('abc') // 0
   str.indexOf('b') // 1
   str.indexOf('ddd') // 6
   str.indexOf('d') // 6
   ```

2. `search()`  查找

   - 主要检索与正则表达式相匹配的值
   - 一个参数，找到返回索引，没找到返回-1

   ```javascript
   const str = 'abcabcddd'
   str.search('abc') // 0
   ```

3. `trim() ` 去除前后空格

   ```javascript
   var str = "  abcde fg h ";
   console.log(str.length);//13
   console.log(str.trim().length);//10
   ```

4. `charAt()`  根据下标返回字符

   ```javascript
   var str = "abcde";
   console.log(str.charAt(0)) //a
   ```

5. `charCodeAt`  根据下标返回字符的ASCLL码

   ```javascript
   var str = "abcde";
   console.log(str.charCodeAt(0)) //97
   ```

6. `fromCharCode()`  将 ASCll 转化为字符

   ```javascript
   console.log(String.fromCharCode(97)) //a
   ```

7. `substr(s1,s2)`  截取字符串

   - 第一个参数是开始截取的索引，第二个参数要截取多少个
   - 只有一个参数，代表从开始截取的位置到最后
   - 返回值是截取的字符串

   ```javascript
   var str = "abcdef";
   console.log(str.substr(0, 5));//abcde
   console.log(str.substr(4));//ef--写一个参数为索引，默认截取字符串该索引后面的所有字符
   console.log(str.substr(-3,2))//从倒数第三个,截取2个
   ```

8. `substring(start,end)` 截取字符串

   * 作用:对字符串进行截取(包前不包后)
   * 参数:start表示截取开始的索引,end表示截取结束的索引,end要大于start,不允许负数
   * 返回:从start到end的字符串,不包含end

   ```javascript
   var str = "abcdef";
   console.log(str.slice(0, 4));//abcd
   console.log(str.slice(3));//def--等价于substring
   ```

9. `slice(start,end)`

   * 作用：对字符串截取，start表示截取的开始元素，end表示截取的截止元素，包前不包后。

   * 返回值：截取的字符串

   * ```javascript
     console.log(str.slice(0,4));//0是起始索引,4是结束索引,不包含4
     console.log(str.slice(4));//表示从4到结束
     console.log(str.slice(-3));//表示倒数第三到最后
     ```

10. `split(s1,s2)`  将字符串转化成数组

    - 第一个参数是根据什么截取，可以是字符串，可以是正则

    ```javascript
    var s3 = "abcdefg";
    console.log(s3.split('')) //转换为['a','b','c','d','e','f','g']
    var s4 = "a,b,cd,e,fg";
    console.log(s3.split(',')) //转换为['a', 'b', 'cd', 'e', 'fg']
    ```

11.`match()`  匹配符合正则的字符串

- 参数是正则表达式
- 返回值是null 或者符合正则的字符串数组

```javascript
var tel = 'dddaaadddcccdddd';
console.log(tel.match(/ddd/)) //['ddd', 'ddd', 'ddd']
```

12. `replace()`  替换

- `replace()`  方法是用替换值（replacement）替换部分子串，或者替换所有匹配的子串。返回值是替换以后的新字符串。

  **语法：**

```javascript
str.replace(regexp|substr, newSubStr|function)
// 第一个参数是： 字符串 或者 正则表达式
// 第二个参数是： 替换的字符串 | 每次都会执行的回调函数
```

- 当第一个参数是字符串的时候，仅第一个匹配项会被替换。

  ```javascript
  const str = 'abcde'
  const newStr = str.replace('a','c')  
  console.log(newStr) // 'cbcde'
  ```

- 当第二个参数是函数的时候，函数的返回值会作为替换的字符串。



#### 二、遍历字符串

1. #### `for` 循环

```javascript
const str = '0123456'
for(var i=0;i< str.length;i++){
  console.log(str[i]);//0 1 2 3 4 5 6
}
```

2. `for...in`

```javascript
for ( const key in str) {
   console.log(key);//0 1 2 3 4 5 6
}
```