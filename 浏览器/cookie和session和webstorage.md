

1. WebStorage和Cookie可以存储在浏览器或者本地，session只能存在服务器
2. Session比Cookie更具有安全性
3. Session占用服务器性能，Session过多，增加服务器压力
4. 单个Cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个Cookie
5. sessionStorage和localStorage虽然也有存储大小的限制，但比cookie大得多，可以达到**==5M==**或更大
6.  sessionStorage、localStorage、cookie都是在浏览器端存储的数据

## Cookie

介绍：

- cookie的内容主要包括：名字、值、过期时间、路径和域。
- 若不设置时间，则表示这个cookie的生命期为浏览器会话期间，关闭浏览器窗口，cookie就会消失。这种生命期为浏览器会话期的cookie被称为会话cookie。
- 会话cookie一般不存储在硬盘而是保存在内存里，当然这个行为并不是规范规定的。若设置了过期时间，浏览器就会把cookie保存到硬盘上，关闭后再打开浏览器这些cookie仍然有效直到超过设定的过期时间。

特性：

- cookie数据存放在客户的浏览器上
- cookie的内容主要包括：名字、值、过期时间、路径和域
- cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑*到安全应当使用session 
- 单个cookie保存的数*据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie 
- 只在设置的cookie过期时间之前有效，即使窗口关闭或浏览器关闭 
- cookie中如果设置了路径参数，那么同一个网站中不同路径下的cookie互相是访问不到的*



## session

介绍：

- 当程序需要为某个客户端的请求创建一个session时，服务器首先检查这个客户端的请求里是否已包含了一个session标识（称为session id），如果已包含则说明以前已经为此客户端创建过session，服务器就按照session id把这个session检索出来使用（检索不到，会新建一个），如果客户端请求不包含session id，则为客户端创建一个session并且生成一个与此session相关联的session id，session id的值应该是一个既不会重复，又不容易被找到规律以仿造的字符串，这个session id将被在本次响应中返回给客户端保存。==保存这个session id的方式可以采用cookie==，这样在交互过程中浏览器可以自动的按照规则把这个标识发送给服务器。

特性：

- session数据放在服务器上 
- session中保存的是对象
- session不能区分路径，同一个用户在访问一个网站期间，所有的session在任何一个地方都可以访问到

- 

## WebStorage

- Web Storage又分为两种： sessionStorage 和localStorage ，即这两个是Storage的一个实例。、
- 提供一种在cookie之外存储会话数据的途径。
- 提供一种存储大量可以跨会话存在的数据的机制。

### localStorage

- 始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据
- 在所有同源窗口中都是共享的
- localStorage则一直将数据保存在客户端本地。

### sessionStorage

- 不在不同的浏览器窗口中共享，即使是同一个页面
- sessionStorage将数据保存在session中，浏览器关闭也就没了；
- 仅在当前浏览器窗口关闭之前有效
- 引入了一个“浏览器窗口”的概念，sessionStorage是在同源的同窗口中，始终存在的数据，也就是说只要这个浏览器窗口没有关闭，即使刷新页面或进入同源另一个页面，数据仍然存在，关闭窗口后，sessionStorage就会被销毁，同时“独立”打开的不同窗口，即使是同一页面，sessionStorage对象也是不同的

## 区别

### cookie和session区别

1. cookie数据存放在客户的浏览器上，session数据放在服务器上 
2. cookie不是很安全，别人可以分析存放在本地的cookie并进行cookie欺骗，考虑*到安全应当使用session 
3. session会在一定时间内保存在服务器上，当访问增多，会比较占用你服务器的性能，考虑到减轻服务器性能方面，应当使用cookie 
4. 单个cookie保存的数*据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie 
5. 建议将登录信息等重要信息存放为session，其他信息如果需要保留，可以放在cookie中 
6. session保存在服务器，客户端不知道其中的信心；cookie保存在客户端，服务器能够知道其中的信息 
7. session中保存的是对象，cookie中保存的是字符串 
8. session不能区分路径，同一个用户在访问一个网站期间，所有的session在任何一个地方都可以访问到，而cookie中如果设置了路径参数，那么同一个网站中不同路径下的cookie互相是访问不到的*

### cookie和webstorage区别

- sessionStorage、localStorage、cookie都是在浏览器端存储的数据
- webstorage是为了更大容量存储设计的，cookie的大小是受限的，并且每次请求一个新的页面的时候cookie都会被发送过去，这样无形中浪费了带宽，另外cookie还需要指定作用域，不可跨域调用。
- web storage拥有setItem,getItem,removeItem,clear等方法，不像cookie需要前端开发者自己封装setCookie，getCookie。 
- 但是cookie也是不可或缺的，cookie的作用是与服务器进行交互，作为http规范的一部分而存在的
- 而web Storage仅仅是为了在本地“存储”数据而生
- webstorage好处
  - 减少网络流量：一旦数据保存在本地之后，就可以避免再向服务器请求数据，因此减少不必要的数据请求，减少数据在浏览器和服务器间不必要的来回传递 
  - 快速显示数据：性能好，从本地读数据比通过网络从服务器上获得数据快得多，本地数据可以及时获得，再加上网页本身也可以有缓存，因此整个页面和数据都在本地的话，可以立即显示 
  - 临时存储：很多时候数据只需要在用户浏览一组页面期间使用，关闭窗口后数据就可以丢弃了，这种情况使用sessionStorage非常方便

### cookie、localStorage和sessionStorage区别

- 共同点
  - 都是保存在浏览器端、且同源的 
- 不同的
  1. cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递，而sessionStorage和localStorage不会自动把数据发送给服务器，仅在本地保存。cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下 
  2. 存储大小限制也不同，**==cookie数据不能超过4K==**，同时因为每次http请求都会携带cookie、所以cookie只适合保存很小的数据，如会话标识。sessionStorage和localStorage虽然也有存储大小的限制，但比cookie大得多，可以达到**==5M==**或更大 
  3. 数据有效期不同，sessionStorage：仅在当前浏览器窗口关闭之前有效；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie：只在设置的cookie过期时间之前有效，即使窗口关闭或浏览器关闭 
  4. 作用域不同，sessionStorage不在不同的浏览器窗口中共享，即使是同一个页面；localstorage在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的 
  5. web Storage支持事件通知机制，可以将数据更新的通知发送给监听者 
  6. web Storage的api接口使用更方便

### 浏览器本地存储和服务器存储的区别

1. 浏览器可以保存一些数据，需要的时候直接从本地存取
2. sessionStorage、localStorage和cookie都是由浏览器存储在本地的数据 
3. 服务器端也可以保存所有用户的所有数据，但需要的时候浏览器要向服务器请求数据。
4. 服务器端可以保存用户的持久数据，如数据库和云存储将用户的大量数据保存在服务器端 
5. 服务器端也可以保存用户的临时会话数据，服务器端的session机制，如jsp的session对象，数据保存在服务器上，
6. 实际上，服务器和浏览器之间仅需传递session id即可，服务器根据session id找到对应用户的session对象，会话数据仅在一段时间内有效，这个时间就是server端设置的session有效期
7. 服务器端保存所有的用户的数据，所以服务器端的开销较大，而浏览器端保存则把不同用户需要的数据分别保存在用户各自的浏览器中，浏览器端一般只用来存储小数据，而非服务可以存储大数据或小数据服务器存储数据安全一些，浏览器只适合存储一般数据

