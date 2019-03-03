[掘金](https://juejin.im/entry/5b4d4721f265da0f926b78c8?utm_source=gold_browser_extension)  
[跨域对接方法总结](https://www.cnblogs.com/CccZss/p/8571115.html)

[浏览器的同源策略](https://developer.mozilla.org/zh-CN/docs/Web/Security/Same-origin_policy)  
[http://www.cnblogs.com/2050/p/3191744.html](http://www.cnblogs.com/2050/p/3191744.html)  
[http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html](http://www.ruanyifeng.com/blog/2016/04/same-origin-policy.html)

# 同源策略

如果两个页面的协议，端口（如果有指定）和域名都相同，则两个页面具有相同的源  
下表给出了相对[http://store.company.com/dir/page.html同源检测的示例](http://store.company.com/dir/page.html同源检测的示例):

| URL | 结果 |
| :--- | :--- |
| [https://store.company.com/secure.html](https://store.company.com/secure.html) | 不同协议 \( https和http \) |
| [http://store.company.com:81/dir/etc.html](http://store.company.com:81/dir/etc.html) | 不同端口 \( 81和80\) |
| [http://news.company.com/dir/other.html](http://news.company.com/dir/other.html) | 不同域名 \( news和store \) |

IE:  
当涉及到同源策略时，Internet Explorer 有两个主要的不同点:

* 授信范围（Trust Zones）：两个相互之间高度互信的域名，如公司域名（corporate domains），不遵守同源策略的限制。
* 端口：IE 未将端口号加入到同源策略的组成部分之中，因此 [http://company.com:81/index.html](http://company.com:81/index.html) 和[http://company.com/index.html](http://company.com/index.html)  属于同源并且不受任何限制。

* jsonp   只能在get请求上

          实现原理是使用script的跨域加载

* CORS        [http://www.ruanyifeng.com/blog/2016/04/cors.html](http://www.ruanyifeng.com/blog/2016/04/cors.html)
* 代理
* 使用HTML5中新引进的window.postMessage方法来跨域传送数据

```
A和B俩个跨域的窗口
a向b发送信息，
window.postMessage("data",'http://B.com'); window 是b窗口的window
在窗口b中监听
window.addEventListener('message', function(event) {
    console.log(event.origin);
    console.log(event.source);
    console.log(event.data);
}, false);
```

* websocket
* 使用window.name来进行跨域
* 通过修改document.domain来跨子域

localstorage和indexDB以源进行分割，每个源都拥有自己单独的存储空间。Cookies 使用不同的源定义方式。一个页面可以为本域和任何父域设置cookie，只要是父域不是公共后缀（public suffix）即可，浏览器都允许给定的域以及其任何子域名\(sub-domains\) 访问 cookie

dom无法获取，ajax请求不能发送

## 前后端通信

1. ajax
2. websocket
3. cors





