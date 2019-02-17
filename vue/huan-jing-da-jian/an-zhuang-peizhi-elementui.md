[elementUI官网](http://element.eleme.io/#/zh-CN/component/quickstart)
# 安装配置看直接看官网,因为我基本直接复制官网的
# 安装
在项目根目录中运行：
~~~
npm i element-ui -S

i 是 install的缩写
-S  --save的缩写,是把此依赖配置到当前目录的package.json中
~~~

![](/assets/screenshot_1528104271475.png)

# 配置方式一(完整引入)
打开src/main.js 添加
~~~
import ElementUI from 'element-ui'
import 'element-ui/lib/theme-chalk/index.css'
Vue.use(ElementUI)
~~~
![](/assets/screenshot_1528104347689.png)

这种配置方式是一次全部加载elementUI组件,使得首页加载数据过大,elementUI提供按需引入
# 配置方式二(按需引入)
借助 **babel-plugin-component**，我们可以只引入需要的组件，以达到减小项目体积的目的
~~~
npm install babel-plugin-component -D

-D 是 --save-dev 的缩写,是把此依赖配置到当前目录的package.json中的dependencies里
~~~
然后，将 .babelrc 修改为：)
~~~
{
  "presets": [["es2015", { "modules": false }]],
  "plugins": [
    [
      "component",
      {
        "libraryName": "element-ui",
        "styleLibraryName": "theme-chalk"
      }
    ]
  ]
}
~~~

接下来，如果你只希望引入部分组件，比如 Button 和 Select，那么需要在 main.js 中写入以下内容：
~~~
import Vue from 'vue';
import { Button, Select } from 'element-ui';
import App from './App.vue';

Vue.component(Button.name, Button);
Vue.component(Select.name, Select);
/* 或写为
 * Vue.use(Button)
 * Vue.use(Select)
 */

new Vue({
  el: '#app',
  render: h => h(App)
});
~~~
完整组件列表和引入方式（完整组件列表以 components.json 为准）

