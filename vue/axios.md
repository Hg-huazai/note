

​	interceptors: 拦截器

http://www.axios-js.com/zh-cn/docs/#axios-config



## 拦截器



1. 在请求或响应被==then==或==catch==处理前拦截它们

   ```vue
   //添加请求拦截器
   axios.interceptors.request.use(function(config) {
   	//在发送请求之前做些什么
   	return config;
   }, function (error) {
   	//对请求错误做些什么
   	return Promise.reject(error);
   });
   
   //添加响应拦截器
   axios.interceptors.response.use(function(respose) {
   	//对响应数据做些什么
   	return response;
   }, function (error) {
   	//对响应错误做些什么
   	return Promise.reject(error);
   });
   ```

   

2. 如果稍后移除拦截器

   ```vue
   const myInterceptor = axios.interceptors.request.use(function () {/*...*/});
   axios.interceptors.request.eject(myInterceptor);
   ```

   

3. 可以自定义axios实例添加拦截器

   ```vue
   const instance = axios.create();
   instance.interceptors.request.use(function () {/*...*/});
   
   ```

   

   