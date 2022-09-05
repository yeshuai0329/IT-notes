##### 一、Flux

> Flux 是一种架构思想，专门解决软件的结构问题。它跟MVC架构是同一类东西，但是更加简单和清晰。Flux存在多种实现（至少十五种）
>
> 只要知道两种：Facebook Flux（官方，不完整的库）    Redux
>
> Redux  跟 React 是配合的最好的。



##### 二、Redux

> Redux 不依赖于 React，但是配合最好的是 React
>
> 还有其他的如：1. Vue+Redux
>
> 						    2.react+Redux
> 					
> 							3.angular + Redux
>
> Redux 底层 还是发布订阅模式

##### 三、为什么要用Redux？

1. 很多非父子通信需要管理
2. 缓存后端数据，减少重复的后端请求，减轻服务器的压力，提高用户体验

##### 四、Redux 的工作流

![image-20220904212524456](https://front-notes.oss-cn-hangzhou.aliyuncs.com/img/image-20220904212524456.png)

##### 五、Redux 起步

###### 1.在 src 目录下创建 redux 文件夹，创建 store.js文件

**+  store.js**

```js
import { createStore } from "redux"

//函数===（传入参数返回一个新状态）
//prevState  老状态
const reducer = (prevState={
  isCollapsed:false//初始状态
},action)=>{
  //action 就是dispatch 传递回来的对象
  //prevState.isCollapsed=payload; Redux 里不能直接修改，因为不能影响老状态。
  //必须深复制一份prevState，然后再修改为新状态。
  let { type, payload } = action
  let newPrevState = { ...prevState }
  switch (type) {
    case 'ye_change_collapsed':
      newPrevState.isCollapsed = payload
      return newPrevState
    case 'ye_roleList':
      newPrevState.roleList = payload
      return newPrevState
    default:
      return prevState
  }
}//redux 里修改状态，只能通过reducer
//payload 是 发布者通过dispatch 方法调用传递回来的参数

const store = createStore(reducer)

exprot default store
```

###### 2.订阅者

1. 首先再订阅者组件中引入 src 下的redux 下的store.js

   ```js
   import store from "redux/store.js"
   
   componentDidMount (){
    this.unscribe = store.subscribe(()=>{
       console.log("我是订阅者Sidmenu"，store.getState())
       this.setState({
         collapsed:store.getState().isCollapsed
       })
     })
   }
   
   //订阅者只能通过store.getState()来获取新的状态
   //必须要设置取消订阅
   
   componentDidUnmount(){
     this.unscribe()
   }
   
   ```

###### 3.发布者

1. 首先在发布者组件中引入 src 下的redux 下的store.js

   ```js
   import store from "redux/store.js"
   
   toggle = ()=>{
     store.dispatch({
       type："ye_change_collapse"
       paload:true
     })
     //dispatch 传递来一个对象
   }
   ```

###### 4.actionPromise 风格异步方式

- **依赖于 redux-promise中间件**
- store.js

```js
import { createStore, applyMiddleware } from 'redux'
import reduxPromis from 'redux-promise'//**依赖于 redux-promise中间件**
import reduxThunk from 'redux-thunk'//依赖于 redux-promise中间件
const reducer = (
  prevState = {
    isCollapsed: false,
    roleList: []
  },
  action
) => {
  let { type, payload } = action
  let newPrevState = { ...prevState }
  switch (type) {
    case 'ye_change_collapsed':
      newPrevState.isCollapsed = payload
      return newPrevState
    case 'ye_roleList':
      newPrevState.roleList = payload
      return newPrevState
    default:
      return prevState
  }
}
//**依赖于 redux-promise中间件**
//依赖于 redux-promise中间件
const store = createStore(reducer, applyMiddleware(reduxPromis, reduxThunk))

export default store

```

- 组件中

```js
//1-1 promise风格 依赖于 redux-promise中间件
actionPromise = ()=>{
  return  axios.get("http://localhost:5000/roles").then(res => {
    return {
      type:"kerwin_save_rolelist",
      payload:res.data
    }// action必须有type属性
  }) 
}
componentDidMount() {
	let roleList = store.getState().roleList
  if(roleList.length===0){
    //走一遍逻辑,把数据存储到store中
    store.dispatch(this.actionPromise()) //dispath 传入一个promise对象（函数），不支持，只支持最简单的对象，需要借助中间件（middleware）
  }else{
    this.setState({
      datalist: roleList
    })
  }
  this.unscribe = store.subscribe(()=>{
    this.setState({
      datalist:store.getState().roleList
    })
  })
}
componentWillUnmount(){
  this.unscribe();
}
```

###### 5.async风格

- **依赖于 redux-promise中间件**
- 组件中

```js
actionAsyncPromise = async ()=>{
  let res = await axios.get("http://localhost:5000/roles")
  return {
    type:"kerwin_save_rolelist",
    payload:res.data
  }
}
```

###### 6.dispatch传入的是一个函数

- 依赖于redux-thunk 中间件
- 组件中

```js
actionThunk = ()=>{
  return (dispatch)=>{
    // console.log(dispatch)
    axios.get("http://localhost:5000/roles").then(res=>{
      dispatch({
        type:"kerwin_save_rolelist",
        payload:res.data
      })
    })
  }
}  

componentDidMount() {
  let roleList = store.getState().roleList
  if(roleList.length===0){
  	store.dispatch(this.actionThunk()) 
  }else{
    console.log("使用缓存数据","缓存只是在内存中，页面一刷新就丢了")
    this.setState({
      datalist: roleList
    })
  }

  this.unscribe = store.subscribe(()=>{
    // console.log("role组件",store.getState().roleList)
    this.setState({
      datalist:store.getState().roleList
    })
  })

}
componentWillUnmount(){
  this.unscribe();
}
```

###### 7.redux模块化

1. **合并子reducer为一个大的reducer**

```js
//从redux 里引入 combineReducers ，合并用
import {createStore, applyMiddleware,compose,combineReducers} from 'redux'
import collapseReducer from './reducers/collapseReducer'
import roleListReducer from './reducers/roleListReducer'
```

2. **合并子reducer为一个大的reducer**

```js
const reducer = combineReducers({
    isCollapsed:collapseReducer,
    roleList:roleListReducer
})
```

3. 

```js
const store =createStore(reducer,{
    isCollapsed :false, //初始状态
    roleList:[],
},applyMiddleware(reduxPromise,reduxThunk))//第二参数， 可以设置
```

4. **子模块 collapseReducer.js**

```js
//只管理 isCollapsed 是 true还是false

const collapseReducer  = (prevState=false,action)=>{
    // console.log(action)
    //payload自动传来要修改成什么值？
    // prevState.isCollapsed = payload

    //深复制prevState,返回修改后的新状态

    let {type,payload} = action
    switch (type) {
        case "kerwin_change_collapse":
            //处理折叠
            let newState = payload
            return newState
        default:
            return prevState //没有匹配到， 返回老状态
    }
}
export default collapseReducer
```

5. **子模块  roleListReducer.js**

```js
//只管理 roleList 是 []

const roleListReducer  = (prevState=[],action)=>{
    // console.log(action)
    //payload自动传来要修改成什么值？
    // prevState.isCollapsed = payload

    //深复制prevState,返回修改后的新状态

    let {type,payload} = action
    switch (type) {
        case "kerwin_save_rolelist":
            //处理 roleList
            // console.log(payload)
            let newState = [...prevState,...payload]
            return newState
        default:
            return prevState //没有匹配到， 返回老状态
    }
}

export default roleListReducer
```







##### 六、React-redux

> 利用了 React 的特效，封装了Redux，实现了自动挡

###### 1.起步

```bash
npm i -S react-redux
```

###### 2.根组件中设置 `Provider`

```js
import React from 'react'
import './App.css'
import BlogRouter from './router/index.js'
import { Provider } from 'react-redux'
function App() {
  return (
    <Provider>
      <BlogRouter />
    </Provider>
  )
}

export default App

```

###### 3.子组件中  mapStateToProps

```javascript
import { connect } from 'react-redux'

const mapStateToProps = (state) => {
  console.log(state)
  return {
    ...state
  }
}
export default connect(mapStateToProps)(withRouter(SideMenu))
```

###### 4.子组件

```js
import { connect } from 'react-redux'

this.props.change({
  type: 'ye_change_collapsed',
  payload: !this.state.collapsed
})

const mapStateToProps = (state) => {
  return { ...state }
}
const mapDispatchToProps = {
  change(obj) {
    return obj
  }
}
export default connect(
  mapStateToProps,
  mapDispatchToProps
)(withRouter(TopHeader))
```