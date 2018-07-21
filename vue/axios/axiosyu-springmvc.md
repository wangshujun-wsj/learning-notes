
## axios  post传参

方式一 map 接收

~~~
this.$axios.post(url, {
    num: that.num,dimensionIds: that.dimensionIds,level: that.level
})
        
springmvc接收:    @RequestBody Map map
~~~
方式二 实体类对象 接收

~~~
this.$axios.post(url, user)
        
springmvc接收:    @RequestBody User user
~~~

方式二 多个参数 接收

~~~
let params = new URLSearchParams();
params.append("password", that.user.password);
params.append("newPassword", that.user.newPassword);

this.$axios.post(url, params)
        
springmvc接收:    updatePassword(String password, String newPassword,
~~~