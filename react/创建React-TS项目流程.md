## React+TS+eslint项目流程

#### 1.使用`create-react-app`创建TS项目文件夹

```bash
$ create-react-app h5web-ts --template typescript //h5web-ts 包名
```

#### 2.项目采用eslint代码检查工具

- eslint采用`eslint`+`standard`

- 下载eslint

  ```bash
  $ npm install eslint --save-dev
  ```

- 设置一个配置文件 `.eslintrc.js`

  ```bash
  $ ./node_modules/.bin/eslint --init
  ```

- 配置文件设置流程

  ```js
  1. How would you like to use ESLint? //你想要怎么使用eslint？
     To check syntax, find problems, and enforce code style √
  2. What type of modules does your project use? //你想要模块怎么导入方式？
     JavaScript modules (import/export) √
  3. Which framework does your project use? //你项目使用的框架？
     React √
  4. Does your project use TypeScript? // 是否需要Typescript？
     Yes √
  5. Where does your code run? // 项目是跑在哪里的
     Browser √
  6. How would you like to define a style for your project? //你想要你的项目是什么风格？
     Use a popular style guide √ //大厂风格
  7. Which style guide do you want to follow? //你想要额外加什么规则？
     standard √
  8. What format do you want your config file to be in? //你想要你的项目遵循什么语言？
     JavaScript √
  9. Would you like to install them now with npm? //是否现在下载依赖？
     Yes √
  ```

- 配置` .eslintrc.js` 文件(TS通用)

  ```javascript
  module.exports = {
    env: {
      browser: true,
      es2021: true
    },
    extends: [
      'plugin:react/recommended',
      'standard'
    ],
    parser: '@typescript-eslint/parser',
    parserOptions: {
      ecmaFeatures: {
        jsx: true
      },
      ecmaVersion: 12,
      sourceType: 'module'
    },
    plugins: [
      'react',
      '@typescript-eslint'
    ],
    rules: {
      semi: ['error', 'never'],
      'no-var': 0, // 禁用var，用let和const代替
      'space-before-function-paren': [
        'error',
        {
          anonymous: 'always',
          named: 'never',
          asyncArrow: 'always'
        }
      ],
      "react/prop-types": 0, // 防止在react组件定义中缺少props验证
      "no-new": 0,
      quotes: 0,
      "no-use-before-define": "off",
      "@typescript-eslint/no-use-before-define": "off"
    }
  ```

- vscode 下载`eslint`插件，并在`setting.json`文件中添加自动修复的命令

  ```json
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
  ```

#### 3.基于`create-react-app`扩展`webpack`支持less

> ​	`create-react-app` 扩展webpack方式有两种：
>
> 	1.	通过 `create-react-app` 内置的指令 `npm run eject`；**强烈不推荐**，会使项目文件目录变得复杂，难以维护。
> 	2.	通过第三方包去扩展webpack；**强烈推荐**

- 基于 `react-app-rewired` 和 `customize-cra` 扩展webpack

  ```bash
  $ npm i react-app-rewired customize-cra --save
  ```

- 在项目根目录下创建 `config-override.js` 配置文件

  ```javascript
  // 这个配置是less-loader @5.0.0版本的配置
  const {
    override,
    addLessLoader,
    fixBabelImports
  } = require('customize-cra')
  
  module.exports = override(
  	// webpack扩展支持less  
    addLessLoader({
      javascriptEnabled: true,
      modifyVars: { '@primary-color': '#1DA57A' },
      sourceMap: true
    }),
    // webpack扩展支持antd组件库按需加载
    fixBabelImports('import', {
      libraryName: 'antd',
      libraryDirectory: 'es',
      style: 'css' // 自动打包相关的样式 默认为 style:'css'
    })
  )
  
  ```

- `less-loader`版本过高，可能会出现报错的问题，把less-loader版本降低即可：

  ```bash
  npm i less less-loader@5.0.0 -S
  ```

#### 4.react项目采用`calssnames`包来做局部作用域

- 下载包

  ```bash
  $ npm i calssnames -S
  ```

- `App.module.less`文件

  ```less
  .App {
    text-align: center;
  }
  
  .app  {
    color: red;
  }
  ```

  

- 在组件文件中引用

  ```tsx
  import React from 'react'
  import style from './App.module.less'
  // 先引入包
  import classnames from 'classnames/bind'
  // 再用引入的包包裹一下
  const cx = classnames.bind(style)
  // 
  const App = () => {
    return (
      <div className={cx('App')}>
        哈哈
      </div>
    )
  }
  
  export default App
  ```

#### 5.使用antd组件库且按需加载

- 下载antd组件库

  ```bash
  $ npm i antd -S
  ```

- 下载按需加载插件 `babel-plugin-import`

  ```bash
  npm i babel-plugin-import -S
  ```

- 在 `config-overrides.js` 文件配置`antd`按需加载

  ```javascript
  // 这个配置是less-loader @5.0.0版本的配置
  const {
    override,
    addLessLoader,
    fixBabelImports
  } = require('customize-cra')
  
  module.exports = override(
  	// webpack扩展支持less  
    addLessLoader({
      javascriptEnabled: true,
      modifyVars: { '@primary-color': '#1DA57A' },
      sourceMap: true
    }),
    // webpack扩展支持antd组件库按需加载
    fixBabelImports('import', {
      libraryName: 'antd',
      libraryDirectory: 'es',
      style: 'css' // 自动打包相关的样式 默认为 style:'css'
    })
  )
  
  ```

- 直接在组件中引入antd组件

  ```javascript
  import { Button, Switch } from 'antd'
  ```

#### 6.安装路由

- 安装路由

  ```bash
  npm i react-router react-router-dom -S
  ```

  

- 配置TS可以访问的路由

  ```bash
  npm i @types/react-router @types/react-router-dom -S
  ```

#### 7.安装redux、react-redux

- 下载redux、react-redux

  ```bash
  npm i redux react-redux -S
  ```

- 在store的createStore方法中要配置devtools插件

  - 在js中

    ```javascript
    const store = createStore(
      reducer,
      window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
    )
    ```

    

  - 在TS中

    ```bash
    $ npm i redux-devtools-extension -S
    ```

    ```typescript
    const store = createStore(
      reducer,
      composeWithDevTools()
    )
    ```

    

    

  





















