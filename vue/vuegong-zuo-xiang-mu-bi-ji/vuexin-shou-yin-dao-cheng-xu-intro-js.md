# 官方文档
[官方文档](https://introjs.com/docs/)
[官方git源码地址](https://github.com/usablica/intro.js/)

# 基本使用

## 安装


```
  npm install intro.js --save
```
## 配置

```
  import '../node_modules/intro.js/introjs.css'
```
##　在页面使用

```
  import introJs from 'intro.js'
  
  写在methods的方法中,mounted()生命周期调用即可
        let intro = introJs();
        intro.setOptions({'prevLabel':'&larr; 上一步','nextLabel':'下一步 &rarr;','skipLabel':'跳过','doneLabel':'完成'}).start();

其他api
        intro.onchange(function(targetElement) {
          console.log("new step");
        });
        intro.oncomplete(function() {
          alert("end of introduction");
        });
        intro.onbeforeexit(function() {
          console.log("on before exit")
          // returning false means don't exit the intro
          return true;
        });
        intro.onexit(function() {
          console.log("exit of introduction");
        });

HTML 里面使用
<div data-step="1" data-intro='快速测评可以使用' ></div>
```
## 基本效果
![](/assets/screenshot_1528166745823.png)

# 高级功能

[官方API](https://introjs.com/docs/intro/api/#api)




