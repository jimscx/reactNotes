## reactNotes
#### react-router 
##### 2.路由的使用
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

.....routes.js
export default (
  <Route component={App}>
      <Route path='/index' component={Home} />
      <Route path='/focus' component={Focus} />
      <Route path='/info' component={Info} />
      <Route path='/supplementInfo/:name/:email/:openId/:labId' component={SupplementInfo} />
  </Route>
.....渲染main.js
import React from 'react';
import Router from 'react-router';
import ReactDOM from 'react-dom';
import createBrowserHistory from 'history/lib/createBrowserHistory';
import routes from './routes';

let history = createBrowserHistory();
ReactDOM.render(<Router history={history}>{routes}</Router>, document.getElementById('app'));

```
##### 2.路由中的参数获取
* 类似于`/home/?id=1`
  使用this.props.location.query.id

* 类似于`/home/:id`
  使用this.props.params.id
 
