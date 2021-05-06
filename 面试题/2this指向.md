啊里this面试题

```js
var name = 222
var a = {
  name: 111,
  say: function (){
    console.log(this.name)
  }
}

var fun = a.say
fun()
a.say()

var b ={
  name: 333,
  say: function(fun){
    fun()
  }
}

b.say(a.say)
b.say = a.say
b.say()
```

分析

```js
//在函数中直接使用
function get(content) {
  console.log(content)
}

get('你好')
相当于
get.call(window,'你好')
```

```js
//但函数作为对象的方法被调用(谁调用我，我就指向谁)
var person = {
  name: '张三',
  run: function (time) {
		console.log(`${this.name} 在跑步 最多${time}min就不行了`)
  }
}
person.run(30)
person.run.call(person,30)
```

