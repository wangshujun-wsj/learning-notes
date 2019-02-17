[原文](https://www.cnblogs.com/zhnaglei/p/7121482.html)
[vue-devtools官方](https://github.com/vuejs/vue-devtools)

使用vue.js devtools遇到的磕磕绊绊
1.首先我们需要在谷歌浏览器扩展程序中点击获取更多

2.在搜索框输入vue.js devtools，点击安装此扩展

3.检查扩展是否开启
我们需要检测我的扩展是否开启，允许文件地址是否访问，如果没有勾选文件地址我们就必须在服务器上访问。
![](/assets/iQZrneE.png)


4.修改插件配置文件
C:\Users\zhanglei\AppData\Local\Google\Chrome\User Data\Default\Extensions\nhdogjmejiglipccpnnnanhbledajbpd\3.1.4_0\manifest.json文件
修改如下：
![](/assets/Xl5KMQY.png)


注意
本人安装时,还需要在main.js添加
```
Vue.config.devtools = true;

```

在浏览器项目页面关闭f12的开发者模式,刷新重新运行的项目页面,再次打开f12开发者模式就可以看到vue
![](/assets/%@2Y(NA%3F49%XN9WA}$QTH.png)

