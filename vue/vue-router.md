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



### 路由守卫

#### 全局导航守卫(`router.beforeEach`)

`router.beforeEach` 注册一个全局前置守卫：	

```js
const router = new VueRouter({ ... })

router.beforeEach((to, from, next) => {
  // ...
})
```

- **`to: Route`**: 即将要进入的目标 [路由对象](https://router.vuejs.org/zh/api/#路由对象)

- **`from: Route`**: 当前导航正要离开的路由

- **`next: Function`**: 一定要调用该方法来 **resolve** 这个钩子。执行效果依赖 `next` 方法的调用参数。

  - **`next()`**: 进行管道中的下一个钩子。如果全部钩子执行完了，则导航的状态就是 **confirmed** (确认的)。

  - **`next(false)`**: 中断当前的导航。如果浏览器的 URL 改变了 (可能是用户手动或者浏览器后退按钮)，那么 URL 地址会重置到 `from` 路由对应的地址。

  - **`next('/')` 或者 `next({ path: '/' })`**: 跳转到一个不同的地址。当前的导航被中断，然后进行一个新的导航。你可以向 `next` 传递任意位置对象，且允许设置诸如 `replace: true`、`name: 'home'` 之类的选项以及任何用在 [`router-link` 的 `to` prop](https://router.vuejs.org/zh/api/#to) 或 [`router.push`](https://router.vuejs.org/zh/api/#router-push) 中的选项。

  - **`next(error)`**: (2.4.0+) 如果传入 `next` 的参数是一个 `Error` 实例，则导航会被终止且该错误会被传递给 [`router.onError()`](https://router.vuejs.org/zh/api/#router-onerror) 注册过的回调

  - ```js
    // BAD   **这里有一个在用户未能验证身份时重定向到 /login 的示例：
    router.beforeEach((to, from, next) => {
      if (to.name !== 'Login' && !isAuthenticated) next({ name: 'Login' })
      // 如果用户未能验证身份，则 `next` 会被调用两次
      next()
    })
    ```

  - 

#### 全局解析守卫 (router.beforeResolve)

- ​	这和 `router.beforeEach` 类似，区别是在导航被确认之前，**同时在所有组件内守卫和异步路由组件被解析之后**，解析守卫就被调用。

#### 全局后置钩子(router.afterEach)

- ​	你也可以注册全局后置钩子，然而和守卫不同的是，这些钩子不会接受 `next` 函数也不会改变导航本身：

- ```js
  router.afterEach((to, from) => {
    // ...
  })
  ```

#### 路由独享的守卫

- ​	可以在路由配置上直接定义 `beforeEnter` 守卫：

- ```js
  const router = new VueRouter({
    routes: [
      {
        path: '/foo',
        component: Foo,
        beforeEnter: (to, from, next) => {
          // ...
        }
      }
    ]
  })
  ```

- 

#### 组件内的守卫

1. ​	路由组件内直接定义以下路由导航守卫

   - `beforeRouteEnter`
   - `beforeRouteUpdate` (2.2 新增)
   - `beforeRouteLeave`

2. ```js
   const Foo = {
     template: `...`,
     beforeRouteEnter (to, from, next) {
       // 在渲染该组件的对应路由被 confirm 前调用
       // 不！能！获取组件实例 `this`
       // 因为当守卫执行前，组件实例还没被创建
     },
     beforeRouteUpdate (to, from, next) {
       // 在当前路由改变，但是该组件被复用时调用
       // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
       // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
       // 可以访问组件实例 `this`
     },
     beforeRouteLeave (to, from, next) {
       // 导航离开该组件的对应路由时调用
       // 可以访问组件实例 `this`
     }
   }
   ```

3. `beforeRouteEnter` 是支持给 `next` 传递回调的唯一守卫。对于 `beforeRouteUpdate` 和 `beforeRouteLeave` 来说，`this` 已经可用了，所以**不支持**传递回调，因为没有必要了。

4. 这个离开守卫通常用来禁止用户在还未保存修改前突然离开。该导航可以通过 `next(false)` 来取消。

   - ```js
     beforeRouteLeave (to, from, next) {
       const answer = window.confirm('Do you really want to leave? you have unsaved changes!')
       if (answer) {
         next()
       } else {
         next(false)
       }
     }
     ```

   - 

#### 完整的导航解析流程

### 点击事件触发路由

```js
methods : {
	handle(){
        //方式一：
        this.$router.push('/about'),
        //方式二:
        this.$router.push({
        // 都可以
        // path: '/about'
           name: 'about'
      })
    }
}

```





