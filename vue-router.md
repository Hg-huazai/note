//$router : 是路由操作对象，只写对象

 //$route : 路由信息对象，只读对象

### query和params的使用区别

假设我们现在需要实现一个路由切换，点击之切换到W组件

并传递一个id值和一个age值

```js
<router-link :to="{ A: 'xxx', query: { xx:'xxx' }}" />
<router-link :to="{ A: 'xxx', parmas: { xx:'xxx' }}" />
routes:{ ??? }
```

对于query和parmas来说

- A用name还是path？
- routes要怎么写？
- url长什么样？

**query：**

```js
name和path都可以用
<router-link :to="{ name: 'W', query: { id:'1234'，age:'12' }}"/>
<router-link :to="{ path: '/W', query: { id:'1234',age:'12' }}"/>

```

```js
//1.前者的routes基于name设置
{
path: '/hhhhhhh', //这里可以任意
name: 'W', //这里必须是W
component: W
}
//然后就把path匹配添加到url上去
url:http://localhost:8080/#/hhhhhhh?id=1234&age=12

//2.后者基于path来设置routes
{
path: '/W', //这里必须是W
name: 'hhhhhhhh', //这里任意
component: W
}
url:http://localhost:8080/#/W?id=1234&age=12

//在接收参数的时候都是使用this.$route.query.id
```

**params**:

```js
<router-link :to="{ name: 'W', params: { id:'1234',age:'12' }}"/>
```

```js
//这里只能用name不能用path，不然会直接无视掉params中的内容
//然后在routes中添加
{
path:'/W/:id/:age',
name:'W',
component:W
}
//这里的name与上面router-link中的name保持一致
//url就取决于这个path的写法http://localhost:8080/#/W/1234/12
//注意，path里面的/w可以任意写，写成/hhhhh也可以
//但是！
//  /:id和/:age不能省略，且不能改名字
//不写的话，第一次点击可以实现组件跳转
//且可以通过this.$route.parmas.id获取到传过来的id值，但如果
//刷新页面，传过来的id值和age值就会丢失
//从这也能看出params比query严格
```









我们运用router-link来写

把需要渲染的东西放到router-view里面渲染

```
<router-view></router-view>
```

### 编程是导航

点击改变路径

### 动态路由

(name)

```js
动态路由：
{
	path: '/login/:name',
	component:login
}

```

```js
监听：   获取动态路由的值
watch: {
    $router(to,from){
        this.name = this.$route.params.name
    }
}
```

### 嵌套路由

```js
{
	path:'/contenBar/:id',
	component: contentBar,
	//嵌套路由
	children:[
		{
            path:'contentBar1',
            component:contentBar1,
        },
        {
            path:'contentBar2',
            component:contentBar2,
        }{
            path:'contentBar3',
            component:contentBar3,
        }
	]
}
```

### 路由重定向

设置的路径不一致(path中没有那个路径的配置)，但是我们希望跳转到同一个页面，或者说是打开同一个组件。这时候我们就用到了路由的重新定向redirect参数

```js
{
	path:'*',
	name: 'any',
	redirect:'/login'   //重定向到login
}
```

### 路由参数传递

```js
//第一种方法
{
	path: '/login/:name',
	component:login
}
//获取动态路由的值
watch: {
    $router(to,from){
        this.name = this.$router.params.name
    }
}
//第二种
{
    path:'/login',
    props:{name:'huage'}
}

获取
<template>
	<div>{{name}}</div>      //huage
</template>
export default {
    methods:{
        
    },
    props:['name']
}
```

### 全局导航守卫（路由守卫）



