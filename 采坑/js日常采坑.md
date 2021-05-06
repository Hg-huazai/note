### 读取对象的属性

```js
var obj = {name: 'h', age: '18'}
//方法一： 
console.log(obj.name); //h
//方法二：   
console.log(obj['name']) //h

//(当要读取的属性是个变量时必需使用方法二)
var name1 = 'name'
console.log(obj.name1);  //undefind
console.log(obj[name1])  //h




```



