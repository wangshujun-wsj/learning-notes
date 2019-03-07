## jQuery和vue的区别

* 数据和视图的分离  解耦 （开放封闭原则）  
  比如我们公司项目里面的 支付方式功能，一个支付金额的input、支付方式的下拉框和一个增加按钮，增加按钮用来在下方增加一个相同的input、下拉框和删除按钮。当使用jQuery实现时，需要监听增加按钮的点击事件，在事件中使用js拼接dom和数据追加到指定页面位置方式完成，数据和视图都会在js中操作。使用vue的话只需要在增加按钮的点击事件中给数组追加一条数据即可，页面上的v-for会自动完成，追加时只操作数据，不用处理视图。

* 以数据驱动视图 只关心数据变化，DOM操作被封装

  接上面的例子，jQuery是操作数据和dom使得视图改变，而vue的方式只是对数据进行处理，视图便会根据数据的结果进行相应改变

## mvvm![](/assets/vue/mvvm.png)

mvvm是 Model、 View、 ViewModel，Model就是js对象，View就是DOM，ViewModel这里是vue，ViewModel用来连接View和Model。View通过dom事件经过ViewModel对Model里的数据进行操作，Model通过数据绑定经过ViewModel对View进行页面显示处理。比如v-show 和一个带click的添加按钮，当点击View视图里面的click事件时，View视图通过ViewModel里的方法改变Model数据中的变量，当变量修改，Model数据通过ViewModel将变量的改变同步到View中，控制v-show的显示和隐藏![](/assets/vue/mvvm1.png)

## vue三要素

### 响应式：vue如何监听到data的每个属性变化？

vue通过Object.defineProperty方法给数据添加get和set方法进行监听

### 模板引擎：vue的模板如何被解析，指令如何处理？

### 渲染：vue的模板如何被渲染成html？以及渲染过程？



