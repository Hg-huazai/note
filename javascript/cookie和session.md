# Cookie、session、localStorage、sessionStorage之间的区别

1. Cookie可以存储在浏览器或者本地，session只能存在服务器
2. Session比Cookie更具有安全性
3. Session占用服务器性能，Session过多，增加服务器压力
4. 单个Cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个Cookie
5. sessionStorage、localStorage、cookie都是在浏览器端存储的数据

## Cookie

- cookie数据存放在客户的浏览器上
- cookie的内容主要包括：名字、值、过期时间、路径和域
- cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑*到安全应当使用session 
- 单个cookie保存的数*据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie 
- 只在设置的cookie过期时间之前有效，即使窗口关闭或浏览器关闭 
- cookie中如果设置了路径参数，那么同一个网站中不同路径下的cookie互相是访问不到的*

## session

- session数据放在服务器上 
- session中保存的是对象
- session不能区分路径，同一个用户在访问一个网站期间，所有的session在任何一个地方都可以访问到

## localStorage

- 始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据
- 在所有同源窗口中都是共享的

## sessionStorage

- 不在不同的浏览器窗口中共享，即使是同一个页面
- 仅在当前浏览器窗口关闭之前有效
- 引入了一个“浏览器窗口”的概念，sessionStorage是在同源的同窗口中，始终存在的数据，也就是说只要这个浏览器窗口没有关闭，即使刷新页面或进入同源另一个页面，数据仍然存在，关闭窗口后，sessionStorage就会被销毁，同时“独立”打开的不同窗口，即使是同一页面，sessionStorage对象也是不同的