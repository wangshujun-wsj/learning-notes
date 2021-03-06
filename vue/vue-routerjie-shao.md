
[vue router官方文档](https://router.vuejs.org/zh/)
完整router/index.js在最后

**component: () =>
      import('@/components/login')是路由懒加载方式**
  [官网路由懒加载](https://router.vuejs.org/zh/guide/advanced/lazy-loading.html#%E6%8A%8A%E7%BB%84%E4%BB%B6%E6%8C%89%E7%BB%84%E5%88%86%E5%9D%97)
# 动态路由
router/index.js 中配置
```
      {
      // id 为自定义,可根据自己的情况更改 如 '/hello/:name
        path: '/hello/:id',
        component: () =>
          import('@/components/router/hello'),
        props: true   // 这个参数为true表示把 :id这个参数放到页面的props属性中
      }
```
html使用
```
      <ul>
        <li>
        <!-- "/hello/1" 会匹配 index.js中的 '/hello/:id' -->
          <router-link to="/hello/1">Go to hello1</router-link>
        </li>
        <li>
          <router-link :to="path='/hello/2'">Go to hello2</router-link>
        </li>
        <li>
          <router-link :to="path='/hello/3'">Go to hello3</router-link>
        </li>
        <li>
          <router-link to="/hello/4">Go to hello4</router-link>
        </li>
      </ul>
```
或者在方法中使用
```
	this.$router.push({
          path: '/hello/2'
        });
```
可在动态路由对应的页面获取 :id 的参数 :id是自定义的,用于获取时使用 
获取URL中
/hello/:id 中的id的结果,使用this.$route.params.id获取
'/hello/:name'  使用this.$route.params.name获取
如果 路由中使用了props: true,那么可以使用props里定义同名变量的形式获取,然后直接当做props的普通属性一样使用
# 嵌套路由
router/index.js 中配置
**注意 子路由的path写法**
在需要使用嵌套子路由的路由里使用 children,将子路由配置在children
子路由会渲染在父路由html中的router-view的位置
```
{
    path: '/router',
    component: () =>
      import('@/components/router/routerMain'),
      // 嵌套子路由
    children: [
      {
        // id 为自定义,可根据自己的情况更改 如 '/hello/:name
        path: '/hello/:id',//这个访问时url是 /hello/:id   
        // path: 'hello/:id, // 这个访问时url是 /router/hello/:id   
        component: () =>
          import('@/components/router/hello')
      }
    ]
  }
```
父路由页面html中要渲染子页面的地方配置router-view
![](/assets/screenshot_1528165407785.png)
展示渲染结果
![](/assets/screenshot_1528165289074.png)

# router-link路由

HTML使用
```
<router-link to="/hello">Go to hello4</router-link>
```
会跳转到router/index.js中的 path为 '/hello' 的路由
router-link默认解析为a标签

# 方法中使用路由
除了使用 <router-link> 创建 a 标签来定义导航链接，我们还可以借助 router 的实例方法，通过编写代码来实现。
```
router.push(location, onComplete?, onAbort?)；
// 项目中使用
this.$router.push({
    path: '/routerQuery',
    query: {id: id} // 路由传参,后边有介绍
});
```
**注意**：在 Vue 实例内部，你可以通过 $router 访问路由实例。因此你可以调用 this.$router.push。

| 声明式   | 编程式   |
| --- | --- |
|  `<router-link :to="...">`  |  `router.push(...)`  |

例如:
点击按钮,触发方法进行跳转路由
![](/assets/screenshot_1528166373964.png)

# 重定向
重定向使用 redirect
本例当 浏览器url为 http://localhost:8085/#/ 时会自动转到http://localhost:8085/#/router
![](/assets/screenshot_1528166745832.png)
# 路由传参
第一种路由传参 (query) 参数显示在url中,使用this.$route.query 获取传参对象
例如 : 
```
	this.$router.push({
            path: '/routerQuery',
            query: {id: id, val: this.banner}
          });
          // 对应页面使用 this.$route.query.id 获取传的 id值
```
第二种路由传参  (params需要在路由中配置name名称),params 不会将参数显示在url中,刷新页面值丢失,name对应 index.js中的路由 name值
使用this.$route.params 获取传参对象
例如 : 
```
	this.$router.push({
            name: 'routerQuery',
            params: {id: id, val: this.banner}
          });
          // 对应页面使用 this.$route.params.id 获取传的 id值
```
动态路由的 :id 也是传参
**query或 params在 router-link和 this.$router.push 中使用方式一致**

router-link 中使用 query或 params进行传参
```
     // 第一种传参 query
     <h2>
        <!-- router-link渲染为a标签 -->
        <!--渲染结果
        <a data-v-3e708a56=""
        href="#/routerQuery?id=1&amp;val=router-link%E5%8F%82%E6%95%B0"
         class="">router-link 路由</a>-->
        <router-link :to="{path:'/routerQuery',query: {id:1,val:'router-link参数' }}">router-link query传参路由</router-link>

      </h2>
      // 第二种传参 params
     <h2>
        <!-- router-link渲染为a标签 -->
        <router-link :to="{name:'routerParams',params: {id:1,val:'router-link参数' }}">
          router-link params传参路由</router-link>
      </h2>
```
路由参数放到props里

```
{
  path: '/',
  ......,
  props: route => ({
    food: route.query.food
  })
}


.vue页面

直接使用props获取,这样路由里的参数就赋值给props里了
props: {
  food: {
    ......
  }
}

```



# 命名路由

app.vue


```
<div>
<header></header>
<router-view/>
<router-view name='email'/>
<router-view name='tel'/>

</div>
```
路由文件

在components 中定义位置,default渲染到没有name属性的router-view上,其他渲染到对应的name上
```
{
  path:'/named',
  components: {
    default: () => import('/components/router/hello'),
    email: () => import('/components/router/email'),
    tel: () => import('/components/router/tel')
  }
}
```
# 路由守卫
## 全局路由守卫
比如登录验证在router/index.js中

例子里面是把路由分成了多个页面
```
import Vue from 'vue'
import Router from 'vue-router'
// 路由存放页面
import routes from './router'

Vue.use(Router)
// 是否登录,值来自后台
const HAS_LOGIN = true;

const router = new Router({
  routes
});
// 前置守卫
router.beforeEach((to, from, next) => {
  // 不是登录页面
  if(to.path !=='/login') {
    // 已登录
    if (HAS_LOGIN) {
      // 放过去
      next();
    } else {
      // 跳转登录页面
      next({path: '/login'})
    }
  } else {
    // 已登录
    if (HAS_LOGIN) {
      // 跳转首页
      next({path: '/index'});
    } else {
      // 放过去
      next();
    }
  }
});
// 后置守卫
router.afterEach((to, from) => {
  
})
export default router;
```
## 路由独享守卫
配置在路由列表的具体路由中

```
{
    path: '/about',
    name: 'about',
    component: () => import('../views/About.vue'),
    
    beforeEnter: (to, from, next) => {
      if(from.path === '/login') {
        console.log("这是从登录页过来的")
      } else {
        console.log("这不是从登录页过来的")
      }
      next();
    }
  }
```
## 组件内守卫


```
beforeRouteEnter(to, from, next) {
    console.log("这里不能使用this,因为还没有进入本页面");
    next(vm => {
      // vm 就是this
      console.log(vm)
    });
  },
  beforeRouteUpdate(to, from, next) {
    // 可以使用this对象
    console.log("动态路由改变 :id 时可触发")
  },
  // 离开守卫
  beforeRouteLeave(to, from, next) {
    // 可以使用this对象
    const leave = confirm("确定离开");
    if (leave) {
      next();
    } else {
      next(false);
    }
  }
```
## 完整的导航流程

1. 导航被触发
2. 在失活的组件(即将离开的页面组件)里调用离开守卫 beforeRouteLeave
3. 调用全局的前置守卫 beforeEach
4. 在重用的组件里调用 beforeRouterUpdate (如果是重用的)
5. 调用路由独享的守卫 beforeEnter
6. 解析异步路由组件
7. 在被激活的组件(即将进入的页面组件)里调用beforeRouteEnter
8. 调用全局的解析守卫 beforeResolve
9. 导航被确认
10. 调用全局的后置守卫 afterEach
11. 触发DOM更新
12. 用创建好的实例调用beforeRouterEnter守卫里传给next的回调函数

# 路由元信息
使用元信息meta 修改页面的title


路由列表里添加meta信息 router/router.js
```
{
    path: '/about',
    name: 'about',
    component: () => import('../views/About.vue'),
    beforeEnter: (to, from, next) => {
      if(from.path === '/login') {
        console.log("这是从登录页过来的")
      }
      next();
    },
    meta: {
      title: '关于'
    }
  }
```
在src/lib/util.js


```
export const setTitle = title => {
  window.document.title = title || 'admin';
}
```
在router/index.js


```
import setTitle from '../lib/util'
router.beforeEach((to, from, next) => {
  // 设置title
  to.meta && setTitle(to.meta.title);
  
  // 不是登录页面
  if(to.path !=='/login') {
    ....
  }
});

```








# 匹配优先级
有时候，同一个路径可以匹配多个路由，此时，匹配的优先级就按照路由的定义顺序：谁先定义的，谁的优先级就最高。

# 完整router/index.js

```
import Vue from 'vue';
import Router from 'vue-router';

Vue.use(Router)

export default new Router({
  routes: [{
    path: '/',
    redirect: {
      path:'/router'
    },
    component: () =>
      import('@/components/login')
  }, {
    path: '/resume',
    name: 'resume',
    component: () =>
      import('@/components/resume/resume')
  }, {
    path: '/router',
    component: () =>
      import('@/components/router/routerMain'),
    // 嵌套子路由
    children: [
      {
        // id 为自定义,可根据自己的情况更改 如 '/hello/:name
        path: '/hello/:id',
        component: () =>
          import('@/components/router/hello')
      }
    ]
  }, {
    path: '/routerQuery',
    name: 'routerQuery',
    component: () =>
      import('@/components/router/routerQuery')
  }, {
    path: '/routerParams',
    name: 'routerParams',
    component: () =>
      import('@/components/router/routerParams')
  }, {
    path: '/watch',
    component: () =>
      import('@/components/demo/watch-computed')
  }, {
    path: '/class',
    component: () =>
      import('@/components/demo/class-style')
  }]
})


```
