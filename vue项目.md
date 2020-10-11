### 使用模版

​	1.使用

		2. 导入
  		3. 注册

```js
<template>
  <div id="app">
    <img src="./assets/logo.png">
    //使用模版
    <HelloWorld />
    <hello />
  </div>
</template>

<script>
   //导入
import HelloWorld from './components/HelloWorld'
import hello from './components/hello'
export default {
  name: 'App',
    //模版注册
  components: {
    HelloWorld,
    hello
  }
}
</script>
```

