# 安装
根目录运行
~~~
npm install axios -S
~~~
# 配置
在src/main.js配置 axios
导入 axios 并在　new Vue()中配置
~~~
import axios from '../node_modules/axios'

Vue.prototype.$axios = axios;
new Vue({
  el: '#app',
  router,
  store,
  axios,
  components: { App },
  template: '<App/>'
})
~~~

简单使用:
~~~
 .then 里是后台返回结果
 .catch 里是网络错误或后台服务器出bug.then方法里出错等等


get方式
this.$axios.get('/user', {
      params: {
        数据
     }
  })
  .then(function (response) {
  })
  .catch(function (error) {
  });

post方式
this.$axios.post('/user' , user)
  .then(function (response) {
  })
  .catch(function (error) {
  });

~~~


vue 中配置跨域访问后台
~~~
	proxyTable: {
      '/api': {
        target: 'http://127.0.0.1:18080', // 后台访问地址
        changeOrigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    },
~~~
![](/assets/screenshot_1528106942310.png)
配置后可直接在npm run dev 时直接访问后台地址
前缀比真实后台是多了个  /api ,就是
~~~
this.$axios.post('/api/login/login', user)
	.then(function (response) {
	})
	.catch(function (error) {
	});
~~~