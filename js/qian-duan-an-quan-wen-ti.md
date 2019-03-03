[8 大前端安全问题（上）伯乐在线](http://web.jobbole.com/92875/)  
[8 大前端安全问题（下）伯乐在线](http://web.jobbole.com/92893/)  
[面试--web安全的理解](https://segmentfault.com/a/1190000011459463)

## csrf

跨站请求伪造

原理：用户登录网站A，会在浏览器保存cookie，当用户访问网站b时，网站b引诱用户点击访问网站A的具有漏洞的接口，访问接口上传cookie，网站A对用户身份重新确认，任发现是合法用户就执行了方法。

![](file:///C:\Users\wang\AppData\Roaming\Tencent\Users\1115693174\QQ\WinTemp\RichOle\5OY[L6%29WJ{MJNWO$82VM[DM.png)



