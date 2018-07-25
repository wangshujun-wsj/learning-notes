# 官方文档
[官方文档](https://introjs.com/docs/)

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
  
  introJs().setOptions({'prevLabel':'&larr; 上一步','nextLabel':'下一步 &rarr;','skipLabel':'跳过','doneLabel':'完成'}).start();
　introJs().addHints();

HTML 里面使用
<div data-step="1" data-intro='快速测评可以使用' ></div>
```
## 基本效果
![](/assets/screenshot_1528166745823.png)








