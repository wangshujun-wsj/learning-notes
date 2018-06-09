~~~
// The Vue build version to load with the `import` command
// (runtime-only or standalone) has been set in webpack.base.conf with an alias.
import Vue from 'vue'
import App from './App'
import router from './router'
// 引入 vuex
import store from './store'
// 引入 axios
import axios from '../node_modules/axios'
// 引入elementUI的样式
import 'element-ui/lib/theme-chalk/index.css'
// 初始化样式
import '../static/css/reset.css'
// 通用样式
import '../static/css/style.css'

Vue.config.productionTip = false;
/* 配置elementUI 按需引入  start*/
/* 本项目中首页用的组件较多,所以在这里引用了较多的组件*/
import {
  Autocomplete,
  Menu,
  Submenu,
  MenuItem,
  MenuItemGroup,
  Row,
  Col,
  Carousel,
  CarouselItem,
  Pagination,
  Message,
  MessageBox,
  Loading,
  Rate,
  Badge,
  Dropdown,
  DropdownMenu,
  DropdownItem
} from 'element-ui';
let arr = [
  Autocomplete,
  Menu,
  Submenu,
  MenuItem,
  MenuItemGroup,
  Row,
  Col,
  Carousel,
  CarouselItem,
  Pagination,
  Loading,
  Rate,
  Badge,
  Dropdown,
  DropdownMenu,
  DropdownItem
];
arr.forEach(function(e) {
  Vue.use(e);
});
Vue.prototype.$message = Message;
Vue.prototype.$loading = Loading.service;
Vue.prototype.$msgbox = MessageBox;
Vue.prototype.$alert = MessageBox.alert;
Vue.prototype.$confirm = MessageBox.confirm;
Vue.prototype.$prompt = MessageBox.prompt;
/* 配置elementUI 按需引入  end*/
// axios.defaults.baseURL = '127.0.0.1:18080'
Vue.prototype.$axios = axios;
/* eslint-disable no-new */
new Vue({
  el: '#app',
  router,
  store,
  axios,
  components: { App },
  template: '<App/>'
});
~~~