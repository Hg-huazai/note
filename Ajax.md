



![image-20200911205406342](C:\Users\Hg-huazai\AppData\Roaming\Typora\typora-user-images\image-20200911205406342.png)



### ajax局部加载，不刷新整个页面

#### jquery-ajax

```js
$.ajax({
    url: 'http://yqw.namicity.cn/yanxuan/app/doctor/loadDoctorList',
    headers: {
        "content-type": "application/x-www-form-urlencoded",
    },
    success: function (data) {
        console.log(data)
    }
})
```

```js
$.post({
    url: 'http://yqw.namicity.cn/yanxuan/app/doctor/loadDoctorList',
    headers: {
        "content-type": "application/x-www-form-urlencoded",
    },
    data: {
        
    }
    success: function (data) {
        console.log(data)
    }
})
```

```js
//两个参数
$.get('http://yqw.namicity.cn/yanxuan/app/doctor/loadDoctorList',function(data){
    console.log(data)
})
```

