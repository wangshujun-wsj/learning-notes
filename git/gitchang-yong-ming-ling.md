[阮一峰git教程](http://www.ruanyifeng.com/blog/2014/06/git_remote.html )


查看用户名和邮箱地址：
~~~
git config user.name

git config user.email
~~~
查看git配置

```
$git config --lis

```

修改用户名和邮箱地址：
~~~
git config --global user.name "username"
git config --global user.email "email"
~~~

远程主机克隆项目
~~~
git clone <版本库的网址>
~~~
该命令会在本地主机生成一个目录，与远程主机的版本库同名。如果要指定不同的目录名，可以将目录名作为git clone命令的第二个参数
~~~
git clone <版本库的网址> <本地目录名>
~~~

一旦远程主机的版本库有了更新（Git术语叫做commit），需要将这些更新取回本地，这时就要用到git fetch命令。
```
git fetch <远程主机名>
```



