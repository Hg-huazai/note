# 需理解的函数

## **obj.hasOwnProperty(prop)**深拷贝有关

- 作用：方法会返回一个布尔值，指示对象**自身属性**中是否具有指定的属性（也就是，是否有指定的键）。

- 参数：

  - prop
  - 要检测的属性的 [`String`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String) 字符串形式表示的名称，或者 [`Symbol`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Symbol)。

- 返回值：用来判断某个对象是否含有指定的属性的布尔值 [`Boolean`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean)。

- 描述：所有继承了 [`Object`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object) 的对象都会继承到 `hasOwnProperty` 方法。这个方法可以用来检测一个对象是否含有特定的==自身属性==；和 [`in`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/in) 运算符不同，该方法会==忽略==掉那些从==原型链上继承到的属性==。

- 备注：即使属性的值是 `null` 或 `undefined`，只要==属性存在==，`hasOwnProperty` 依旧会返回 `true`。

  - ```js
    o = new Object();
    o.propOne = null;
    o.hasOwnProperty('propOne'); // 返回 true
    o.propTwo = undefined;
    o.hasOwnProperty('propTwo'); // 返回 true
    ```

  - 

- 举例：

  - ```js
    function ObjWithProto(){
        this.foo = 'foo_val'
    }
    ObjWithProto.prototype.bar = 'bar_val'
    var dict = new ObjWithProto()
    dict.foobar = 'foobar_val'
    
    dict.hasOwnProperty('foo') // true
    dict.hasOwnProperty('foobar') // true
    dict.hasOwnProperty('bar') // false  bar是原型上的属性
    ```

  - ```js
    再来看 for…in , 遍历一个对象的可枚举属性
    for(let i in dict){
        console.log(i)
    }
    //foo
    // foobar
    // bar        //原型链上的bar也获取到了
    ```

  - ```js
    为了遍历一个对象的所有属性时忽略掉继承属性，使用hasOwnProperty()来过滤该对象上的继承属性。
    
    for(let i in dict){
        if(dict.hasOwnProperty(i)){
          //bar属性被过滤掉了
           console.log(i)
        }
    }
    //foo
    //foobar    
    
    ```

  - ```js
    再来看看原型连上的一个继承
    function ObjWithProto(){
            this.foo = 'foo_val'
        }
        ObjWithProto.prototype.bar = 'bar_val'
    
        function Person(){
            this.name = 'Person_name'
        }
        Person.prototype = new ObjWithProto()
        var _child = new Person()
    
        for(let i in _child){
            console.log(i)
          //name
        	//foo
        	//bar
        }
    
        console.log('------ this is a line -------')
    
        for(let i in _child){
            if(_child.hasOwnProperty(i)){
                console.log(i)   //name
            }
        }
        _child.hasOwnProperty('name') // true
        _child.hasOwnProperty('foo') // false
        _child.hasOwnProperty('bar') // false
    
        
       
    ```

  - 

- ```
  用for...in循环会获取到原型链上的可枚举属性，不过可以使用hasOwnProperty()方法过滤掉。
  ```


  