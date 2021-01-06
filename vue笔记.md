JSON-handle    谷歌插件

vsc  debug    -》   f5快捷键     ctrl+shift+d

双向数据绑定原理：采用数据劫持结合发布者-订阅者模式的方式，通过Object.defineProperty()来劫持各个属性的setter，getter，在数据变动时发布消息给订阅者，触发相应的监听函数。

## filter/map/reduce   一定要去了解

filter：过滤，返回数组     如获取name==’lihua‘

map：  返回数组         获取所有的id返回一个数组

reduce： 返回一个结果  



移动端滑动（iscroll）不维护了不推荐

移动端滑动（better-scroll）github有文档连接



#### es6

```js
for (let i in books) {
    
}
for (let book of books) {
    
}
```





### v-once: 

v-once指令是指展示一遍，不会改变（不会再随data的数据改变了）

```html
<view v-once>{{message}}<view>
```



### 计算属性：

```html
<view>{{allname}}</view>
```

```js
const app = new Vue({
    el:'#app',
    data: {
        name1: '你好呀！',
        name2: '我不好！',
         
    },
    //方法
    methops: {
    
	},
    //计算属性
    computed: {
       allname: function(){
			return this.name1 + this.name2
        }             
    }
})
```



computed会比methops的性能会好一点，methops调用几次就会执行几次，没有缓存的，computed会进行判断，如果发现数据有改变的话就会重新调用

#### 

#### 计算属性的setter和getter

```
const app = new Vue({
    el:'#app',
    data: {
        name1: '你好呀！',
        name2: '我不好！',
         
    },
    //方法
    methops: {
    
	},
    //计算属性
    computed: {
    //简写
       //allname: function(){
		//   return this.name1 + this.name2
       //} 
       
       //原型
       allname: function(){
       	set: function(){
       	
       	},
       	//一般只需要getter就可以了（一般没有set属性的，只读属性）
       	get: function(){
       		return this.name1 + this.name2
       	}
       }
    }
})
```



vue视频的P25

es5 只有function有作用域

es5的var是没有块级作用域的，es6的let是有块级作用域的

## es6

##### 作用域

if 与 for 没有块级作用域   所以要用let   要么就要用闭包了

```js
for(var i = 0; i<5; i++){
    console.log(i)
    //闭包(函数有一个属于自己的作用域的与外面的没有影响)   //外面的for的i对函数的i没有任何的影响的，因为调用函数的时候就已经传入i了，不会在改变了// 甚至函数的参数i，可以是其他东西，num、name...	
    (function(i){
        console.log(i)
    })(i)
}
```

块级作用域的理解(个人)

```js
//es5没有块级作用域
for(var i = 0; i<5; i++){
    console.log(i)
    (function(i){
        console.log(i)
    })(i)
}
```



### 数组的响应式

#### 1.push();   向数组后面追加元素

#### 2.pop();   删除数组最后一个元素

#### 3.shift();    删除数组第一个元素

#### 4.unshift();  在数组最前面添加元素可添加多个 ; unshift(...item);/ unshift('a','b','c')

#### 5.splice();  删除/替换/插入元素

第一个参数： 是表示从数组的第几个元素开始

删除元素：第二个参数，传入你要删除几个元素(如果没有传，就删除后面所有的元素)

替换元素： 第二个参数，表示我们要替换几个元素，后面（后面参数）是用于替换前面的元素

插入元素： 第二个参数，传入0，并且后面（后面的参数）跟上要插入的元素

{

#### 	vue 内部的 set替换方法

##### 	set(要修改的对象，索引值，修改后的值)

##### 	vue.set(this.array, 0, 'aaa';)

}

#### 6.sort();   排序	

#### 7.reverse();   数组反转



#### 8.通过索引来修改元素不是响应式的；





#### 背景图片高斯模糊

#### css

#### filter： blur(10rpx);   数值越大越模糊





#### promise是个类 所以需要new   （异步操作可使用promise处理）

参数本身是个函数   

而函数里还有两个参数（resolve，reject）  resolve是成功，reject是拒绝

而这两个参数本身 又是函数

```js
new promise ((resolve,reject)=>{
    resolve()
}).then(()=>{
    
})
```



链式编程

```js
//第一次处理请求
new promise ((resolve,reject)=>{
    resolve()
}).then(()=>{  //第一次拿到结果
    
    //第二次处理请求
     retuen new Promise((resolve,reject)=>{
         resolve()
     })
}).then(()=>{
    //第二次拿到数据
})
```

```JS
//并发请求（同时到达再做相应处理）都请求成功后才会调用then
Promise.all({
    new promise ((resolve,reject)=>{
    	resolve()
	}),
    new promise ((resolve,reject)=>{
    	resolve()
	})
}).then(()=>{
    
})
```





## Vuex

##### 父传子  props

npm install vuex --save

```js
const store = new Vuex.Store({
    state:{
        //状态 其他页面获取（$store.state.counter）
        counter: '100
    },
    mutations: {
        //	只要修改state都会经过mutations
        //方法   获取其他页面事件($store.commit('addition'))   谷歌跟踪（Devtools)
        add(){
            $store.commit('addition') 
        }
    },
    actions: {
        
    },
    getters: {
        //类似于计算属性   其他页面获取（$store.getters.pingfang）
        pingfang(state){
            return state.counter * state.counter
        }
    },
    modules: {
        
    }
})
```





# axios

安装插件

1.npm install axios --save（上线后还需要使用）

2.导入(main.js) ： import axios from 'axios',

3.使用： 

```js
axios({
    url:'httpbin.org/'    //线上网络测试接口httpbin.org/     或者postwoman/postman
})
```



axios返回的是个promise，所以请求成功的时候(内部会调用resovle的)我们直接调用.then()即可

服务器返回的是data，其他的是axios框架的

axios最基本使用

```	js
axios({
    url:'httpbin.org/data?type=pop&page=3',
    method: 'get/post'
}).then(res=> {
    console.log(res)
})
```

```js
axios({
    url:'httpbin.org/data',
    method: 'get/post',
    //专门针对get请求的参数拼接
    params: {
        type: 'pop',
        page: 3
    }
}).then(res=> {
    console.log(res)
})
```

![image-20200823235435682](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200823235435682.png)

axios发送并发请求

```
axios.all([axios({}),axios({})]).then(res=>{})
```

```JS 
//定义全局(公共)
//defaults 默认
//params   url查询对象
axios.defaults.baseURL = 'http://123.207.32.32:8080'
axios.defaults.timeout = 5000   //超时

axios.all([axios({
    url:'/home/data'
}),axios({
    url:'/home/data',
    params: {
        type: 'pop',
        page: 5
    }
})]).then(res=>{})
```

method: 'get'  对应得是params

method: 'post'  对应得是data

```
axios({
	url: '',
	method: 'get',
	params: {
		type: 'pop',
		page: 3
	}
	
})
axios({
	url: '',
	method: 'post',
	data: {
		type: 'pop',
		page: 3
	}
	
})
```

创建对应的axios的实例

```js
const instance1 = axios.create({
    baseURL: 'http://123.207.32.32:8000',
    timeout: 5000
})

instance1({
    url: '/home/multidata'
}).then(res =>{
    console.log(res);
})
```

封装request

因为不是default导出 ，所以要加{ }



```js
//request.js    文件封装
import axios from 'axios'
export function request(config) {
    return new Promise((resolve, reject) => {
        //创建axios实例
        const instance = axios.create({
            baseURL: 'http://123.207.32.32.8000',
            timeout: 5000
        })
    })
    //发送真正的网络请求
   // 方法一
    instance(config)
    .then(res => {
       resolve(res)
    })
    .catch(err => {
        reject(err)
    })
}



//main.js   //使用request
import {request} from "./network/request";   //因为不是default导出 ，所以要加{ }
request({
    url: '/home/multidata'
}).then(res => {
    console.log(res)
}).catch(err => {
    console.log(err)
})
```

```js
方法二  (推荐使用)
//request.js    文件封装

import axios from 'axios'
export function request(config) {

   //创建axios实例
        const instance = axios.create({
            baseURL: 'http://123.207.32.32.8000',
            timeout: 5000
        })
        
    //发送真正的网络请求
    // 因为axios返回的本身就是个promise了，所以方法一是多余的
    return instance(config)
}



//main.js   //使用request

import {request} from "./network/request";   //因为不是default导出 ，所以要加{ }

request({
    url: '/home/multidata'
}).then(res => {
    console.log(res)
}).catch(err => {
    console.log(err)
})
```



## vue-router

此处要注意$router和$route     $route 是属于当前活跃状态

```html
<router-link></router-link>
<router-view></router-view>
```





![image-20200829220830885](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829220830885.png)



![image-20200829222200861](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829222200861.png)

![image-20200829222830552](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829222830552.png)

![image-20200829222103574](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829222103574.png)



tag=“button”    默认是a标签，  可以tag=“div”

![image-20200829223309033](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829223309033.png)

replace   没有返回功能

![image-20200829223524787](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829223524787.png)

被选中会增加一个class（router-link-active）

![image-20200829224140698](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829224140698.png)



通过点击事件跳转router

replace也是没有返回功能

![image-20200829225143554](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829225143554.png)

获取路由的属性（abc）

![image-20200829231021378](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829231021378.png)

![image-20200829230854366](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829230854366.png)

![image-20200829235755645](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200829235755645.png)



参数传参

![image-20200830000039259](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200830000039259.png)

![image-20200830000135486](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200830000135486.png)