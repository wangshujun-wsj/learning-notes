组件的通信 ：provide / inject

[https://juejin.im/book/5bc844166fb9a05cd676ebca/section/5bc845435188255c533655f4](https://juejin.im/book/5bc844166fb9a05cd676ebca/section/5bc845435188255c533655f4)

在父页面router-view使用v-if="isRefresh"控制显示隐藏

```
<router-view v-if="isRefresh"></router-view>
```

data定义

```
 isRefresh: true
```

methods中定义

```
      refresh () {
        this.isRefresh  = false
        this.$nextTick(function () {
          this.isRefresh = true
        })
      }
```

在methods同级定义provide

```
    provide () {
      return {
        refresh: this.refresh
      }
    },
```

在需要刷新的页面使用inject注入refresh方法，inject和methods同级

```
inject: ['refresh']
```

![](file:///C:\Users\wang\AppData\Roaming\Tencent\Users\1098803106\QQ\WinTemp\RichOle\48T6U~CWR]N[JBF~0%286{C]H.png)



