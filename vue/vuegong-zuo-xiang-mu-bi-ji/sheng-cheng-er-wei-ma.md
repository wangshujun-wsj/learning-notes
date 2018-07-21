使用插件 VueQr 

npm 安装
~~~
npm install vue-qr --save
~~~
使用页面导入

~~~
import VueQr from 'vue-qr'
components: {VueQr}
~~~

~~~
// logoSrc 是logo图片存放地址, url 是二维码扫描进入的页面地址,margin是设置无空白边距(默认20,图片显示在左上角,出现很多空白)
<vue-qr :logoSrc="logoSrc" :text="url" :margin="0"></vue-qr>
~~~

下载二维码功能在 base64图片下载里面



