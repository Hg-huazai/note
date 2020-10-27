![image-20200912142211834](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200912142211834.png)

#### jquery 建议用1.0的最终版本，支持ie678    （大公司都在用）

如果把js写在head里面的话，需要写的函数，不然会找不到想要的dow(节点、操作对象)

原生js

```html
<head>
    <script>
    	window.onload = function(){
            
        }
    </script>
</head>
```

jq

```html
<head>
    <script>
    	$(document).ready(function(){
            
        })
    </script>
</head>
```

简写

```html
<head>
    <script>
    	$(function(){
            console.log('hello')
        })
    </script>
</head>
```



```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="./jquery.min.js"></script>
    <script>
        $(function () {
           let id1 = $('#id1')
           let text = $('.text').html();   //你好
            
        })

    </script>
</head>

<body>
    <div id="id1">
        <p class="text">你好</p>
        <input type="button" id="button1" value="提交哦">
    </div>
    
</body>

</html>
```

## jQuery 效果

### 显示和隐藏

#### hide() 和 show()

$(*selector*).hide(*speed,callback*);

$(*selector*).show(*speed,callback*);

可选的 speed 参数规定隐藏/显示的速度，可以取以下值："slow"、"fast" 或毫秒。

可选的 callback 参数是隐藏或显示完成后所执行的函数名称。

下面的例子演示了带有 speed 参数的 hide() 方法：

```js
$("button").click(function(){
  $("p").hide(1000);
});

$("div").hide(1000,"linear",function(){
      alert("Hide() 方法已完成!");
    });
```

#### toggle()

通过 jQuery，您可以使用 toggle() 方法来切换 hide() 和 show() 方法。

显示被隐藏的元素，并隐藏已显示的元素：

```js
$("button").click(function(){
  $("p").toggle();
});
```

### 淡入淡出

#### fadeIn()   fadeOut()   

#### fadeToggle()   fadeTo()

- fadeIn()   用于淡入已隐藏的元素。
- fadeOut()   方法用于淡出可见元素。
- fadeToggle()   方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。
- fadeTo()   方法允许渐变为给定的不透明度（值介于 0 与 1 之间）fadeTo() 没有默认参数，必须加上 slow/fast/Time 

```js
$("button").click(function(){
  $("#div1").fadeToggle();
  $("#div2").fadeToggle("slow");
  $("#div3").fadeToggle(3000);
});

注意：fadeTo() 没有默认参数，必须加上 slow/fast/Time 
$("button").click(function(){
  $("#div3").fadeTo("slow",0.7);
});
```

### 滑动方法

#### slideDown()

#### slideUp()

#### slideToggle()

- slideDown()   方法用于向下滑动元素。
- slideUp()     方法用于向上滑动元素。
- slideToggle()    方法可以在 slideDown() 与 slideUp() 方法之间进行切换。

语法

```js
$(selector).slideDown(speed,callback);
$(selector).slideUp(speed,callback);
$(selector).slideToggle(speed,callback);

//可选的 speed 参数规定效果的时长。它可以取以下值："slow"、"fast" 或毫秒。
//可选的 callback 参数是动画完成后所执行的函数名称。
```

运行

```js
$("#flip").click(function(){
  $("#panel").slideToggle();
});

```

### 动画

#### animate()

##### animate() 方法 用于创建自定义动画。

您甚至可以把属性的动画值设置为 "show"、"hide" 或 "toggle"：

语法：

```js
$(selector).animate({params},speed,callback);
```

运行：

```js
$("button").click(function(){
    $("div").animate({
      height:'toggle'
    },1000);
  });
```

##### animate() - 使用队列功能

```js
$("button").click(function(){
  var div=$("div");
  div.animate({height:'300px',opacity:'0.4'},"slow");
  div.animate({width:'300px',opacity:'0.8'},"slow");
  div.animate({height:'100px',opacity:'0.4'},"slow");
  div.animate({width:'100px',opacity:'0.8'},"slow");
});
```

### 停止动画

#### stop() 方法

stop() 方法  用于停止动画或效果，在它们完成之前。

语法：

```
$(selector).stop(stopAll,goToEnd);
```

可选的 stopAll 参数规定是否应该清除动画队列。默认是 false，即仅停止活动的动画，允许任何排入队列的动画向后执行。

可选的 goToEnd 参数规定是否立即完成当前动画。默认是 false。

因此，默认地，stop() 会清除在被选元素上指定的当前动画。

### Callback 方法

实例在隐藏效果完全实现后再回调函数:

(完成动画后再执行回调函数)

```
$("button").click(function(){
  $("p").hide("slow",function(){
    alert("段落已经被隐藏了");
  });
});
```

###  链(Chaining)

**提示：** 这样的话，浏览器就不必多次查找相同的元素。

实例：("p1" 元素首先会变为红色，然后向上滑动，再然后向下滑动：)

```js
$("#p1").css("color","red").slideUp(2000).slideDown(2000);
```



## jQuery-HTML

### 捕获

- #### text() - 设置或返回所选元素的文本内容

- #### html() - 设置或返回所选元素的内容（包括 HTML 标记）

- #### val() - 设置或返回表单字段的值

- #### attr() 方法用于获取属性值。

```js
//获得链接中 href 属性的值：
$("button").click(function(){
  alert($("#runoob").attr("href"));
});
```

### 设置内容和属性

- #### text() - 设置或返回所选元素的文本内容

- #### html() - 设置或返回所选元素的内容（包括 HTML 标记）

- #### val() - 设置或返回表单字段的值

- #### attr() 方法也用于设置/改变属性值。

- #### text()、html() 以及 val() 的回调函数
回调函数有两个参数：被选元素列表中当前元素的下标，以及原始（旧的）值。然后以函数新值返回您希望使用的字符串。
```js
$("#btn1").click(function(){
    $("#test1").text("Hello world!");
});
$("#btn2").click(function(){
    $("#test2").html("<b>Hello world!</b>");
});
$("#btn3").click(function(){
    $("#test3").val("RUNOOB");
});
```

