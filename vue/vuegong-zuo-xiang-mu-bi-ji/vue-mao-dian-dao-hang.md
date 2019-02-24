```
   <div >
        <div >
            <span>
              按拼音查找：
            </span>
          <span
                v-for="(item,index) of brands" :key="index" @click="goNavigation('brand', index)"></span>
        </div>
        <div v-for="(item,index) of brands" :key="index">
          <div :id="'brand-'+index" ></div>
        </div>
      </div>
```

在锚点位置加点击方法@click="goNavigation\('brand', index\)"

定位位置加id      &lt;div :id="'brand-'+index" class="pinyin-navigation-div"&gt;{{item.首字母}}&lt;/div&gt;

```
      // 拼音导航锚点
      goNavigation(type, index) {
        // 其他无关内容省略
        
        let selector = this.$el.querySelector("#" + type + "-" + index);
        document.documentElement.scrollTop = selector.offsetTop - 80
      },
```



