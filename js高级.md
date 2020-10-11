# js高级

1. ### 基础总结深入

2. ### 函数高级

3. ### 面向对象高级

4. ### 线程机制与事件机制



```js
//函数回调
document.getElementById('hanshu').onclick = function(){
        alert(this.innerHTML)
      };

// 定时器回调函数
        setTimeout(() => {
          alert('定时器回调函数')
        }, 2000);

//匿名函数自调用
	(function (){
        console.log('')
    })()
```

