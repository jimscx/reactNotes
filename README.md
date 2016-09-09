## react使用总结

### 1. react中的注释
同JavaScript注释一样
* 单行注释 // comments
* 多行注释 /* comments */
* React推荐在父组件与子组件间写注释的时候，要加{} 类似于这样{/* comments */}.




### 2. 路由的基本使用 [react-router](https://github.com/reactjs/react-router)
2.1. 首先使用根路由组件 `import Router from 'react-router';`然后使用{} 的形式把你定义的路由规则加载进来
```
import React from 'react';
import Router from 'react-router';
import ReactDOM from 'react-dom';
import createBrowserHistory from 'history/lib/createBrowserHistory';//h5路由形式去掉 # 
import routes from './routes';
let history = createBrowserHistory();
ReactDOM.render(<Router history={history}>{routes}</Router>, document.getElementById('app'));
```
2.2. 定义自己的路由规则
```
export default (
  <Route component={App}>
      <Route path='/index' component={Home} />
      <Route path='/focus' component={Focus} />
      <Route path='/info' component={Info} />
      <Route path='/supplementInfo/:name/:email/:openId/:labId' component={SupplementInfo} />
  </Route>
  )
```
2.3. 定义根组件
```
.....App.js组件
import React from 'react';
class App extends React.Component {
	render() {
		return (
			<div className="page">
				{this.props.children}
			</div>
		);
	}
}
```
2.3 Link的使用 
Link组件用于取代<a>元素，生成一个链接，允许用户点击后跳转到另一个路由。它基本上就是<a>元素的React版本，可以接收Router的状态。
* import { Router, Route, Link } from 'react-router'
```
this.state.users.map(user => (
              <li key={user.id}><Link to={`/user/${user.id}`}>{user.name}</Link></li>
            ))
```
2.4 react 路由中参数的获取
* 类似于`/home/?id=1`
  使用`this.props.location.query.id`

* 类似于`/home/:id`
  使用`this.props.params.id`

 
