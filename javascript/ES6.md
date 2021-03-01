	IE 10+

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

### find()、findIndex()与filter()

1. find()：

   1. 查找第一个符合条件的数组元素；

   2. 参数是一个回调函数；

   3. 回调函数中写出要查找的条件

   4. 条件为true时，返回改元素；

   5. 没有符合条件的元素，返回值为undefined

   6. 回调函数有三个参数： 

      1. value： 当前数组元素；
      2. index： 当前索引的值；
      3. arr：被查找的数组

   7. ```js
      const myArr=[1,2,3,4,5,6];
      var v=myArr.find((value,index,arr)=>{
          return index==4
      });
      console.log(v);// 5
      ```

   8. ```js
      const myArray = [1,2,4,5,6];
      var A= myArray.find(value=>{
      	value>4
      });
      console.log(A)   //5
      var B= myArray.find(value=>{
      	value>10
      });
      console.log(B)     //undefined
      ```

2. findIndex():

   1. findIndex()与find()的使用方法相同。
   2. 当条件为true的时候，findIndex()返回的是索引值，而find()返回的是值;
   3. 没有符合条件是： findIndex()返回的是-1，find()返回的是undefined；
   4. findIndex() 也可以接受三个参数，和find()一样

3. filter():

   1. filter()和find()使用方法也相同，同样可接受三个参数；

   2. 当条件为true时，返回的是**数组**，数组内是所有满足条件的元素；

   3. 如果条件都不满足的话，则返回一个空数组；

   4. ```js
      var userArr = [
          { id:1,userName:"laozhang"},
          { id:2,userName:"laowang" },
          { id:3,userName:"laoliu" },
      ]
      console.log(userArr.filter(item=>item.id>1));
      //[ { id: 2, userName: 'laowang' },{ id: 3, userName: 'laoliu' } ]
      ```

   5. ```js
      数组去从
      var myArr = [1,3,4,5,6,3,7,4];
      console.log(myArr.filter((value,index,arr)=>arr.indexOf(value)===index));
      //[ 1, 3, 4, 5, 6, 7 ]
      ```

   6. 

4. 总结：
   `1.find()与findIndex()参数与用法相同，不同的是find返回元素，findIndex返回索引；找不到时find返回undefined，findIndex返回-1.`
   `2.findIndex()与indexOf()，findIndex比indexOf更强大一些，可以通过回调函数查找对象数组，indexOf只能查找数组中指定的值，不过indexOf可以指定开始查找位置的索引`

### 数组的.every()方法

​	every() 方法用于检测数组所有元素是否都符合指定条件（通过函数提供）。

every() 方法使用指定函数检测数组中的所有元素：

- 如果数组中检测到有一个元素不满足，则整个表达式返回 *false* ，且剩余的元素不会再进行检测。
- 如果所有元素都满足条件，则返回 true。
- 空数组调用.every(),   返回值是true

**注意：** every() 不会对空数组进行检测。

**注意：** every() 不会改变原始数组。

购物车全选视频：https://www.bilibili.com/video/BV1nE41117BQ?p=90

```js
//购物车全选问题
当商品全都选中的时候，全选才扣上；（也就是v.checked都为true时候）
空数组调用every(),会返回false；

const allChecked = cart.length?cart.every(v=>v.checked):false;
```





### includes()

1. ​	查找字符串是否包含 "Runoob":

   1. ```js
      var str = "Hello world, welcome to the Runoob。";
      var n = str.includes("world");      //true
      ```

2. 检测数组 *site* 是否包含 runoob :

   1. ```js
      let site = ['runoob', 'google', 'taobao'];
       
      site.includes('runoob'); 
      // true 
       
      site.includes('baidu'); 
      // false
      ```

   2. 