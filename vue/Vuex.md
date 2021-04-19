## Vuex

- ##### 父传子  props


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

#### 修改state属性(官方推荐)

```vue
const state = {
  num:0
}
const mutations = {
  SET_NUM(state, payload) {
    state.num= payload;
  },
}
export default new Vuex.Store({
  state,
  mutations
})
```

```vue
<template>
  ...
</template>
<script>
  export default{
    data(){
      return{
        num:1
      }
    },
    methods:{
	  doSomething(){
	    this.$store.commit('SET_NUM',this.num);
	  }	
	}
  }
</script>
```

#### 修改state属性(不推荐)

(直接修改state的方式，因为这样不能使用vuex的浏览器插件来跟踪状态的变化，不利于调试。)

```vue
//组件里直接修改state也是生效的
doSomething(){
   this.$store.state.num = this.num;
 }
```

