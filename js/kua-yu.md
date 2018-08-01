[掘金](https://juejin.im/entry/5b4d4721f265da0f926b78c8?utm_source=gold_browser_extension)
[跨域对接方法总结](https://www.cnblogs.com/CccZss/p/8571115.html)

[浏览器的同源策略](https://developer.mozilla.org/zh-CN/docs/Web/Security/Same-origin_policy)
http://www.cnblogs.com/2050/p/3191744.html
# 同源策略
如果两个页面的协议，端口（如果有指定）和域名都相同，则两个页面具有相同的源
下表给出了相对http://store.company.com/dir/page.html同源检测的示例:

| URL | 结果 |
|-----|-----|-----|
|https://store.company.com/secure.html|不同协议 ( https和http )|
|http://store.company.com:81/dir/etc.html|不同端口 ( 81和80)|
|http://news.company.com/dir/other.html|不同域名 ( news和store )|
 
IE:
当涉及到同源策略时，Internet Explorer 有两个主要的不同点:

* 授信范围（Trust Zones）：两个相互之间高度互信的域名，如公司域名（corporate domains），不遵守同源策略的限制。
* 端口：IE 未将端口号加入到同源策略的组成部分之中，因此 http://company.com:81/index.html 和http://company.com/index.html  属于同源并且不受任何限制。


1. jsonp   只能在get请求上
2. CORS        http://www.ruanyifeng.com/blog/2016/04/cors.html
3. 代理
4. 使用HTML5中新引进的window.postMessage方法来跨域传送数据
5. 使用window.name来进行跨域
6. 通过修改document.domain来跨子域


