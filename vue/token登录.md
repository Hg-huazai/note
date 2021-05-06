https://blog.csdn.net/weixin_33943347/article/details/91450659

开写之前先捋一下整理思路：

- 首次登录时，后端服务器判断用户账号密码正确之后，根据用户id、用户名、定义好的秘钥、过期时间生成 token ，返回给前端；
- 前端拿到后端返回的 token ,存储在 localStroage 和 Vuex 里；
- 前端每次路由跳转，判断 localStroage 有无 token ，没有则跳转到登录页，有则请求获取用户信息，改变登录状态；
- 每次请求接口，在 Axios 请求头里携带 token;
- 后端接口判断请求头有无 token，没有或者 token 过期，返回401；
- 前端得到 401 状态码，重定向到登录页面。





axios请求拦截

使用token请求

在登录的时候保存token

```js
window.sessionStorage.setItem('cat_token', res.data.token)
```

发起请求时带上token

```js
function getInfo(url, params) {
  const token = window.sessionStorage.getItem('cat_token')
  axios.post(url, params, { headers: {  Authorization: ` ${token}`  } }).then((res) => {
    console.log(res)
  })
}
```

