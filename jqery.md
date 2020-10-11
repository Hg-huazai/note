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

