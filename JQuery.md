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

#### hide() 

#### show()

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

#### fadeIn()   用于淡入已隐藏的元素。

#### fadeOut()   方法用于淡出可见元素。

#### fadeToggle()   方法可以在 fadeIn() 与 fadeOut() 方法之间进行切换。

#### fadeTo()   方法允许渐变为给定的不透明度（值介于 0 与 1 之间）fadeTo() 没有默认参数，必须加上 slow/fast/Time 

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

#### Callback 方法

实例在隐藏效果完全实现后再回调函数:

(完成动画后再执行回调函数)

```js
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

#### text() - 设置或返回所选元素的文本内容

#### html() - 设置或返回所选元素的内容（包括 HTML 标记）

#### val() - 设置或返回表单字段的值

#### attr() 方法用于获取属性值。

```js
//获得链接中 href 属性的值：
$("button").click(function(){
  alert($("#runoob").attr("href"));
});
```

### 设置内容和属性

#### text() - 设置或返回所选元素的文本内容

#### html() - 设置或返回所选元素的内容（包括 HTML 标记）

#### val() - 设置或返回表单字段的值

#### attr() 方法也用于设置/改变属性值。

#### text()、html() 以及 val() 的回调函数
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

$("#btn1").click(function(){
    $("#test1").text(function(i,origText){
        return "旧文本: " + origText + " 新文本: Hello world! (index: " + i + ")"; 
    });
});
```

### 添加元素

#### append() - 在被选元素的结尾插入内容

#### prepend() - 在被选元素的开头插入内容

#### after() - 在被选元素之后插入内容

#### before() - 在被选元素之前插入内容

```js
$("p").append("追加文本");
```

#### 通过 append() 和 prepend() 方法添加若干新元素

#### 通过 after() 和 before() 方法添加若干新元素

```js
function appendText(){
    var txt1="<p>文本-1。</p>";              // 使用 HTML 标签创建文本
    var txt2=$("<p></p>").text("文本-2。");  // 使用 jQuery 创建文本
    var txt3=document.createElement("p");
    txt3.innerHTML="文本-3。";               // 使用 DOM 创建文本 text with DOM
    $("body").append(txt1,txt2,txt3);        // 追加新元素
}
```

### 删除元素

#### remove() - 删除被选元素（及其子元素）

#### empty() - 从被选元素中删除子元素

```js
$("#div1").remove();	
$("#div1").empty();
```

#### 过滤被删除的元素

jQuery remove() 方法也可接受一个参数，允许您对被删元素进行过滤

```js
下面的例子删除 class="italic" 的所有 <p> 元素：
$("p").remove(".italic");
```

### CSS类

#### addClass() - 向被选元素添加一个或多个类

#### removeClass() - 从被选元素删除一个或多个类

#### toggleClass() - 对被选元素进行添加/删除类的切换操作

#### css() - 设置或返回样式属性

```JS
下面的例子展示如何向不同的元素添加 class 属性。当然，在添加类时，您也可以选取多个元素
$("button").click(function(){
  $("h1,h2,p").addClass("blue");
  $("div").addClass("important");
});
```

### CSS方法

#### css() 方法设置或返回被选元素的一个或多个样式属性

```js
$("p").css("background-color","yellow");

$("p").css({"background-color":"yellow","font-size":"200%"});
```

### 尺寸

很容易处理元素和浏览器窗口的尺寸。

(https://www.runoob.com/jquery/jquery-dimensions.html)

#### width()

#### height()

#### innerWidth()

#### innerHeight()

#### outerWidth()

#### outerHeight()



## jQuery-遍历

### jQuery 遍历 - 祖先

#### parent()   该方法只会向上一级对 DOM 树进行遍历。

#### parents()   方法返回被选元素的所有祖先元素

#### parentsUntil()   方法返回介于两个给定元素之间的所有祖先元素。

```js
下面的例子返回介于 <span> 与 <div> 元素之间的所有祖先元素：
$(document).ready(function(){
  $("span").parentsUntil("div");
});
```

### jQuery 遍历 - 后代

#### children()   方法返回被选元素的所有直接子元素。该方法只会向下一级对 DOM 树进行遍历。

#### find()   方法返回被选元素的后代元素，一路向下直到最后一个后代。	

#### 也可以使用可选参数来过滤对子元素的搜索。

```js
下面的例子返回类名为 "1" 的所有 <p> 元素，并且它们是 <div> 的直接子元素：
$(document).ready(function(){
  $("div").children("p.1");
});
```

### jQuery 遍历 - 同胞(siblings)

#### siblings()  返回被选元素的所有同胞元素。

#### next()   返回被选元素的下一个同胞元素。

#### nextAll()   返回被选元素的所有跟随的同胞元素。

#### nextUntil()   返回介于两个给定参数之间的所有跟随的同胞元素。

#### prev()

#### prevAll()

#### prevUntil()

```js
siblings()
也可以使用可选参数来过滤对同胞元素的搜索。
下面的例子返回属于 <h2> 的同胞元素的所有 <p> 元素：
$(document).ready(function(){
  $("h2").siblings("p");
});
```



### jQuery 遍历- 过滤

#### first() 方法返回被选元素的首个元素。

#### last() 方法返回被选元素的最后一个元素。

#### eq() 方法返回被选元素中带有指定索引号的元素。

#### not() 方法返回不匹配标准的所有元素。

```js
$(document).ready(function(){
  $("p").eq(1);
});
```

```js
not() 方法与 filter() 相反。
下面的例子返回不带有类名 "url" 的所有 <p> 元素：
$(document).ready(function(){
  $("p").not(".url");
});
```



## jQuery - AJAX 

### load() 方法

#### load() 方法从服务器加载数据，并把返回的数据放入被选元素中。

```js
$(selector).load(URL,data,callback);
```

必需的 *URL* 参数规定您希望加载的 URL。

可选的 *data* 参数规定与请求一同发送的查询字符串键/值对集合。

可选的 *callback* 参数是 load() 方法完成后所执行的函数名称。



可选的 callback 参数规定当 load() 方法完成后所要允许的回调函数。回调函数可以设置不同的参数：

- *responseTxt* - 包含调用成功时的结果内容
- *statusTXT* - 包含调用的状态
- *xhr* - 包含 XMLHttpRequest 对象

```js
$("button").click(function(){
  $("#div1").load("demo_test.txt",function(responseTxt,statusTxt,xhr){
    if(statusTxt=="success")
      alert("外部内容加载成功!");
    if(statusTxt=="error")
      alert("Error: "+xhr.status+": "+xhr.statusText);
  });
});
```



### AJAX get() 和 post() 方法

*GET* - 从指定的资源请求数据

*POST* - 向指定的资源提交要处理的数据

#### $.get() 方法

```js
语法：
$.get(*URL*,*callback*);

必需的 URL 参数规定您希望请求的 URL。
可选的 callback 参数是请求成功后所执行的函数名。

第二个参数是回调函数。第一个回调参数存有被请求页面的内容，第二个回调参数存有请求的状态。
```

```js
$("button").click(function(){
  $.get("demo_test.php",function(data,status){
    alert("数据: " + data + "\n状态: " + status);
  });
});
```

#### $.post() 方法

**语法:**

```js
$.post(*URL,data,callback*);
```

必需的 *URL* 参数规定您希望请求的 URL。

可选的 *data* 参数规定连同请求发送的数据。

可选的 *callback* 参数是请求成功后所执行的函数名。

第三个参数是回调函数。第一个回调参数存有被请求页面的内容，而第二个参数存有请求的状态。

```js
$("button").click(function(){
    $.post("/try/ajax/demo_test_post.php",
    {
        name:"菜鸟教程",
        url:"http://www.runoob.com"
    },
    function(data,status){
        alert("数据: \n" + data + "\n状态: " + status);
    });
});
```



## 其他

### noConflict() 方法   释放对 $ 标识符的控制

释放$符号

```js
释放$符号
$.noConflict();
jQuery(document).ready(function(){
  jQuery("button").click(function(){
    jQuery("p").text("jQuery 仍然在工作!");
  });
});
```



自定义jquery简写

```js
您也可以创建自己的简写。noConflict() 可返回对 jQuery 的引用，您可以把它存入变量，以供稍后使用。请看这个例子：
var jq = $.noConflict();
jq(document).ready(function(){
  jq("button").click(function(){
    jq("p").text("jQuery 仍然在工作!");
  });
});
```



### JSONP 教程

