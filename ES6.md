​	IE 10+

​	引入babel.js

在线编译（需要时间，不是很推荐）

```html
<script src="browser.js"></script>
<script type="text/babel"></script>
```



### 数组

map()         映射



reduce()    汇总  （一堆出来一个）

```js
var Array = [2,4,5,6,7,8,9]
      var sum = Array.reduce(function(tmp,item,index){
        return tmp+item
      });
      console.log(sum)   //41
```



filter()        过滤

```js
var Array = [2,4,5,6,7,8,9]
//大于6的留下
      var newArray = Array.filter(item=>{
        if(item>6){	
          return true      // 为true就留下
        }
      });
      console.log(newArray)   //[7,8,9]
```



forEach()  循环(迭代)

```js
var Array = [2,4,5,6,7,8,9]
//大于6的留下
      Array.forEach(item=>{
          console.log(item)
      }) 
```

### json

```js
json标准写法:
	1.只能用双引号
    2.所有的名字都必须用引号包起来
    let json = {"name": 'hauge', "age": 21}
JSON.stringify(json)   //json=》字符串
JSON.parse()    //字符串=》json
```

### 字符串

1.两个新方法

​     startsWith()   以什么开头

​     endsWith()  以什么结尾

```js
let str = 'http:// 12jdjdkjkjj'
        if(str.startsWith('http://')){
          console.log(true)
        }
		 if(str.endsWith('http://')){
          console.log(true)
        }
```

2.字符串模版

​    字符串连接

```js
let a =12;
let str = `ab${a}bg`
console.log(str)  //ab12bg
```

### 面向对象

1.class关键字、构造器和类分开了

2.class里面加方法

```js
//es5
function User(name,pass){
    this.name = name;
    this.pass = pass;
}
User.prototype.showName = function(){
    console.log(this.name)
}
User.prototype.showPass = function(){
    console.log(this.pass)
}
var ul = new User('huage',123);
        ul.showName();   //huage
        ul.showpass();    //123
```



```js
//es6
class User{
          constructor(name, pass){
            this.name = name;
            this.pass = pass;
          }
          showName(){
            alert(this.name)
          }
          showpass(){
            alert(this.pass)
          }
        }
        var ul = new User('huage',123);
        ul.showName();   //huage
        ul.showpass();    //123
```



继承：

```js
super  => 超类（父类）
class VipUser extends User {
    constructor(name, pass, level){
        super(name, pass);
        this.level = level;
    }
    showLevel(){
        console.log(this.level);
    }
}
var v1 = new VipUser('blue','123', 2);
v1.showName();
v1.showName();   
v1.showpass();   
```

### generator   (生成器)   

​		--中间可以停

​		yield；     （放弃）

​		踹一步走一步

generator里面有一个next()方法

```js
function *show(){
    console.log('a');
    
    yield;
    
    console.log('b')
}

let genObj = show();
genObj.next();   //a
genObj.next();   //b
```



