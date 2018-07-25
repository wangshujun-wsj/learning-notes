# 基本使用

## 安装


```
npm install intro.js --save
```
## 配置

```
import '../node_modules/intro.js/introjs.css'
```
##　使用

```
  import introJs from 'intro.js'
        introJs().setOptions({'prevLabel':'&larr; 上一步','nextLabel':'下一步 &rarr;','skipLabel':'跳过','doneLabel':'完成'}).start();

        introJs().addHints();
```









