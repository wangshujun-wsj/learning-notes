```
    <div id="app">
        <span v-bind:title="message" v-bind:dat-myXX="message" v-bind:data-myXX="pData">
          {{ message   }}
        </span>
        <p>{{   pData}}</p>
        <p>{{   message}}</p>
        <p>{{   pData}}</p>
    </div>


```



```

    var app = new Vue({
        el: '#app',
        data: {
          message: '这是message',
          pData: '这是pData'
        }
      })

      function Vue (option) {
          var context = document.querySelector(option.el);
          var data = option.data;
          var html = context.innerHTML;
          var regex = /(\{\{\s*([\w]+)\s*\}\})/g;
         while (regex.exec(html)) {
 
            // 要替换的内容
            var value = data[RegExp.$2];
            var len = RegExp.$1.length;
            // 要替换的内容
            // g全局替换提高性能 ({{}} 里面内容一致会同时一次全部替换掉,
            // 里面变量两边空格不一致会认为是两个,就要等到循环
            // 到它的位置才会替换)
            html = html.replace(new RegExp(RegExp.$1,'g'), value);
            regex.lastIndex -= len - value.length;
          }
          regex = /(v\-bind:([\w\-]+)=\"([\w]+)\")/g;
          while (regex.exec(html)) {
            var value = RegExp.$2+"=\""+data[RegExp.$3]+"\"";
            var len = RegExp.$1.length;
            html = html.replace(new RegExp(RegExp.$1,'g') ,value);
            regex.lastIndex -= len - value.length;
          }
          console.log(html)
          context.innerHTML = html;
        }


```

