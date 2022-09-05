### 一、函数的this指向

1. #### this指向函数的调用对象

   ```javascript
   let obj = {
       a: 1,
       foo: function() {
      console.log(this)
       }
   }
   obj.foo() // this => obj
   ```

2. #### this指事件的调用对象

3. #### 在构造函数中this指向示例对象

   ```javascript
   function Parent(name, age) {
       console.log(this)
       this.name = name
       this.age = age
   }
   let person = new Parent('小明', 19)
   // 在构造函数中this指向示例对象
   ```

4. #### 在prototype原型的方法中，this指向实例对象

   ```javascript
   function Parent(name, age) {
       this.name = name
       this.age = age
   }
   
   Parent.prototype.sayHi = function() {
           console.log(this) 
   }
   // 在prototype原型的方法中，this指向实例对象
   ```

5. #### 找不到函数的调用的this指向window

   ```javascript
   function test() {
    console.log(this)
   }
   test() // this => window
   
   let obj = {
       a: 1,
       foo: function() {
      console.log(this)
       }
   }
   var fn = obj.foo
   fn() // this => window
   ```

6. #### 箭头函数没有自己的this，它的this指向上下文中的this(即所处环境的this)