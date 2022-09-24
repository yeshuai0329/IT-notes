## 1、项目简介





## 2、初始化项目

### 2.1、初始化环境

- `@vue/cli 5.0.8`
- `node v12.22.12`

```bash
vue creat v2-admin
```



## 3、项目目录



## 4、实现功能

#### 1、使用 `ant-design-vue@1.7.8` 组件库

> ​	`ant-design-vue@1.7.8` 是支持 vue2.0 的最后一个版本的

##### 1.1、采用 **按需加载** 的方式引入

```bash
$ npm install ant-design-vue@1.7.8 --save
$ npm install babel-plugin-import --save-dev
```

- 在 `bable.config.js` 中添加

```js
plugins: [
  [
    "import",
    { libraryName: "ant-design-vue", libraryDirectory: "es", style: true },
  ]
]
```

- `and-design-vue` 按需加载的是 `less`,所以需要下载`less` `less-loader`依赖,但是要注意版本号，这里容易报错。

```bash
$ npm install less@3.0.0 less-loader@5.0.0 --save-dev
```



##### 1.2、常用组件作为全局组件引入项目

- 在 `main.js` 中

```js
...
import AntDesignVue from '@/AntDesignVue'

// 引入全局注册的 ant-design-vue 的组件
Vue.use(AntDesignVue)
...
```

- 在 AntDesignVue 文件中

```js
import { Button, Input } from 'ant-design-vue'

const GlobalComponents = [
  Button,
  Input
]

export default (Vue) => {
  GlobalComponents.forEach((component) => {
    Vue.component(component.name, component)
  })
}
```

- **上述方式实际上就是给vue注册全局组件插件**



#### 2、 项目换肤

##### 2.1、 官方配置在 `vue.config.js` 文件中

> ​	此种方法是每次在项目重新构建的时候才会加载 `vue.config.js`,缺点就是每次都要重新启动项目，不能在线更换。

```js
const { defineConfig } = require('@vue/cli-service')

module.exports = defineConfig({
  transpileDependencies: true,
  css: {
    loaderOptions: {
      less: {
        javascriptEnabled: true,
        modifyVars: {
          'primary-color': '#007ac3',// 全局主色
        },
      }
    }
  }
})
```



#### 3、配置额外的环境变量

> ​	默认vue-cli 支持三种环境变量： development\test\production
>
> ​	需要配置环境变量信息的话：
>
> ​		1、在根目录建 `.env.development` 文件内配置开发环境变量
>
> ​		2、在根目录建 `.env.test` 文件内配置测试环境变量
>
> ​		3、在根目录建 `.env.test` 文件内配置生产环境变量
>
> ​	自定义环境变量：
>
> ​		1、在根目录建 `.env.[环境变量名]`， 重点：自定义环境变量一定要在 `.env.[环境变量名]` 文件内写 `NODE_ENV=环境变量名`, 否则不生		   效。
>
> ​	同时要在`package.json` 中配置对应的启动脚本

```json
{
  "scripts": {
    "start": "vue-cli-service serve --mode development",
    "start:test": "vue-cli-service serve --mode test",
    "start:pre": "vue-cli-service serve --mode pre",
    "start:pro": "vue-cli-service serve --mode production",
    "build": "vue-cli-service build --mode pro",
    "lint": "vue-cli-service lint"
  },
}
```



## 5、报错总结

> v2-admin 和 node-server的 报错都可以在这里查找一下

#### 1、v2-admin

##### 001、`template` 蓝色波浪线问题

![image-20220918233032492](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220918233032492.png)

**解析：**

- 在 `jsconfig.json` 的文件中 `vueCompilerOptions` 中配置 `"jsx": "preserve"`

- ```json
  {
    "compilerOptions": {
      "jsx": "preserve",
    }
  }
  ```

  

##### 002、`and-design-vue` 按需加载报错

`报错 .bezierEasingMixin(); ^ Inline JavaScript is not enabled. Is it set in your options...`

**解决办法：**

- 需要下载对应的`less` `less-loader` 版本，这里经过测试`less@3.0.0` `less-loade@5.0.0`

  ```bash
  $ npm install less@3.0.0 less-loader@5.0.0 --save-dev 
  ```

-  同时 `vue.config.js` 中的less的 `javascriptEnabled` 要开启

  ```js
  const { defineConfig } = require('@vue/cli-service')
  
  module.exports = defineConfig({
    transpileDependencies: true,
    css: {
      loaderOptions: {
        less: {
          javascriptEnabled: true
        }
      }
    }
  })
  ```



##### 003、`a-modal` 控制台报错

![image-20220919124857151](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220919124857151.png)

**解决办法**

注册 Modal 的时候，将：

```javascript
Vue.component(Modal.name: Modal)
```

改为：

```javascript
Vue.use(Modal)
```



##### 004、组件注册报错问题



#### 2、node-server 

###### 1、JWT 报错

![image-20220922113212210](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220922113212210.png)

解决方法：

```js
const jsonwebtoken = require('jsonwebtoken')
const SECRET = 'yedashuaiyyds'
const expiresIn = '12h'

const JWT = {
  sign: (id) => {
    return jsonwebtoken.sign(id, SECRET, { expiresIn })
  },
  verify(token) {
    try {
      return jsonwebtoken.verify(token, SECRET)
    } catch (e) {
      return false
    }
  }
}

module.exports = JWT
```

这里的参数改成对象形式传递进去

![image-20220922113426061](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220922113426061.png)