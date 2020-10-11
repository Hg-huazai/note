## AMD模块  依赖require

![image-20200920232701811](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200920232701811.png)

```html
//index.html主文件入口
//data-main   是js的(主模块)     src是require的模块路径
<script data-main="js/main.js" src="js/require.js"></script>
```



```js
//main.js  入口主文件

(function (){
    requirejs.config({
        baseUrl: "js/",  //基本的路径，出发的跟目录
        baths: {  //配置路径
            dataService: './modules/dataService',
            alerter: './modules/alerter',     //例子： alerter里依赖dataService模块
            jquery: './libs/jquery-1.10.1',   //注意jquery模块暴露的是小写
            angular: './libs/angular'  //angular需要单独配置(下方)
        },
        shim: {
            angular: {
                exports: 'angular'
            }
        }
    });

    requirejs(['alerter','angular'],function (alerter,angular) {
        alerter.showMsg();
        console.log(angular);
    })
})
```

```js
//alerter.js
//定义有依赖的模块
define(['detaService','jquery'],function (dataService, $) {
    let msg = 'alerter.js';
    function showMsg() {
        console.log(msg,dataService.getName());
    }
    $.('body').css('bockground','pink');
    
    //暴露模块
    return {showMsg}
})


```



## babel   (es6 ->es5)





安装jquery   版本1的最高版本

npm install jquery@1

npm install jquery     默认安装最新的版本