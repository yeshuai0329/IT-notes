# Use Redux

## 一、`Redux` 简介

> `Redux` 是 `JavaScript` 状态管理容器。
>
> `React` 跟 `Redux` 没有什么直接的联系。就像 `java` 和` JavaScript` 之间。因为 `redux` 在 `react` 中使用起来比较好用，所以常选取 `redux` 作为 `react` 的状态管理容器。

- **优点：**

  - 可以集中管理数据，多组件共享数据。
  - 唯一的数据源，只能通过纯函数来修改。

- **缺点：**

  - 实现原理是 发布订阅模式，`dispatch` 会触发给纯函数中`type`相同的操作，细粒度不够。
  - 需要手动监听，并且组件销毁取消监听。写起来比较麻烦。

- **`Redux` 的使用流程**

  ![image-20210308162611618](/Users/yesshuai/Library/Application Support/typora-user-images/image-20210308162611618.png)

## 二、`Redux` 的三大原则

- ### 单一数据源

  整个应用的 `state` 被储存在一棵 `object tree` 中，并且这个` object tree` 只存在于唯一一个 `store` 中。

- **`state`是只读的**  

  唯一改变 `state` 的方法就是触发 `action`， `action` 是一个用于描述已发生事件的普通对象。

- **使用纯函数来执行修改**  

  为了描述 `action` 如何改变 `state tree`，你需要编写 `reducer`。

## 三、`Redux` 使用步骤

1. 安装 `Redux`

   ```bash
   $ npm i redux --save
   ```

2. 创建 `store`

   > 这个文件主要是为了抛出创建好的 `store` 实例

   ```js
   import { createStore } from 'redux'
   import reducer from './reducer'
   
   const store =createStore(reducer)
   
   export default store
   ```

3. 创建 `reducer` 纯函数

   > `reducer` 纯函数，接收 `defaultState` 和 `action` 并返回一份全新的 `state`。 最后暴露这个函数，给到创建` store` 时 使用

   ```js
   const defaultState ={}
   
   export default （state=defaultState, action）=> {
     if (action.type === 'ADD_SHOP') {
       let newState = JSON.parse(JSON.stringify(state)) // 这里要对数据做深拷贝
       ///这里做添加操作
       return  newState
     }
     return state
   }
   ```

4. 在组件中使用

   ```js
   1. //引入store
   	import store from ’......‘  
   2. //通过store身上的getState()方法获取store中的状态
   	this.state =　｛
   		name: store.getState().name
   	｝
   3. //通过store身上的dispatch 方法获取，出发action，改变redux中的状体
   	store.dispatch({
       type:'ADD_SHOP', //type是必传参数
       value: xxx			//是要传入的值
     })
   4. //在组件创建时候监听改变 
   	unsubscribe = store.subscribe(() => {
       this.setState(store.getState())
     })
   5. //在组件销毁时候取消监听
   	this.unsubscribe()
   ```

## 四、`react-redux`

> `Redux` 是状态管理容器，`react-redux`是一款 `redux` 的插件，`react-redux` 依赖 `redux`,所以使用`react-redux` 要先下载 `redux`包。
>
> 如果说做个比喻的话，`redux` 是一款手动挡车型，那么`react-redux` 则是一款自动档车型。
>
> `react-redux` 帮助开发者完成了状态的订阅和取消订阅的步骤。

1. 安装 `react-redux`

   ```bash
   $ npm i react-redux --save
   ```

2. 使用

   ```js
   1. //在入口文件引入store
   	import store from ’......‘  
   2. //在入口文件引入 Provider 组件，包裹在项目根组件的zuiwaiceng
   	ReactDOM.render(
     <Provider store={store}>
       <BrowserRouter>
         <App />
       </BrowserRouter>
     </Provider>
     ,
     document.getElementById('root')
   )
   3. //在需要用到状态的组件  引入高阶组件包裹住组件
   import { connect } from 'react-redux'
   
   
   export default connect(参数一，参数二)(组件)
   
   //参数一：
   mapStateToProps = (state) => {
     return {
       name: state.name
     }
   }
   //参数二：
   mapDispatchToProps = (dispatch) => {
     return {
       changeHomeEnglish: (paylod) => {
         dispatch({
           type: "ADD_SHOP"
           paload
         })
       }
     }
   }
   ```

## 五、拆分 `reducer`

> 当项目越做越大的时候，如果所有的状态都保存在一个reducer里就会特别庞大复杂。所以一般做项目都会把reducer 拆分成小模块的reducer。

1. 总得 `reducer`

```js
import { combineReducers } from 'redux'
import langreducer from './reducers/langreducer'

export default combineReducers({
  language: langreducer
})
```

2. `langreducer`

```js
import { combineReducers } from 'redux'
import login from './reducers/loginlangreducer'
import home from './reducers/homelangreducer'
import topup from './reducers/topuplangreducer'

export default combineReducers({
  login,
  home,
  topup
})
```

3. `homelangreducer`

```js
import home from '../../../../../lang/zh_CN/home'
import * as actionTypes from '../../../../actions/language/actiontypes'

const defaultState = {
  ...home
}

export default (state = defaultState, action) => {
  if (action.type === actionTypes.CHANGE_HOME_ENGLISH) {
    let newState = JSON.parse(JSON.stringify(state))
    newState = action.payload
    return newState
  }
  return state
}

```

## 六、`redux` 异步

> Redux 的操作流程是同步的代码，如果需要有异步的程序，那么就需要使用到中间件。

异步中间件：

- `redux-thunk`
- `redux-saga`
- `redux-promise`

1. `redux-thunk`

   > 使用redux-thunk 中间件，相当于对store.dispatch 进行了重写

   ```js
   const next = store.dispatch
   store.dispatch = function (action) {
   	if (typeof action === 'function') {
       action(next, store.getState)
     } else {
       store.dispatch(action)
     }
   }
   ```

   







