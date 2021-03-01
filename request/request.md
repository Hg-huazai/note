```js
const http = (router, data = {}, method, contentType, token = {}) => {
	let language = uni.getStorageSync("locale")
	language == 'zh' ? language = 'zh-cn' : language
	// 返回promise
	return new Promise((resolve, reject) => {
		uni.request({
			url: `${router}`,
			data: data,
			method: method,
			header: {
				'Content-Type': `${contentType}`,
				'token': `${token}`,
				'Accept-Language': language
			},
			success: (data) => {
				// 将结果抛出
				resolve(data)
			},
			error: (error) => {
				uni.showModal({
				    title: 'Tips',
				    content: 'Network error, please try again later!'
				});
			}
		})
	})
}

module.exports = {
	http
}
```

