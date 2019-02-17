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
获取特定分支

```
git fetch <远程主机名> <分支名>

git fetch origin master
```

### 取回远程仓库的变化，并与本地分支合并

```
git pull [remote] [branch]
```
### 上传本地指定分支到远程仓库

```
git push [remote] [branch]
```

## 配置SSH密钥
1、查看是否已经有了ssh密钥：cd ~/.ssh
如果没有密钥则不会有此文件夹，有则备份删除

2、直接回车
```
Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):

```
3、重复输入密码

```
Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
```
4、将SSH密钥添加到ssh-agent

```
ssh-agent bash

ssh-add id_rsa
```
// 图解过程
![](/assets/JR8WJ7F$M}5E1@}][FFI`37.png)

5、添加到github
进入C:\Users\【你的用户名】\.ssh  复制id_rsa.pub 里的内容

进入github网站的 settings（右上角最后一个图）选择左侧SSH and GPG keys标签
点击 New SSH key 按钮   将复制的id_rsa.pub 的内容粘贴到key里

# idea 切换SVN和git
修改项目下.idea目录的vcs.xml配置文件中的<mapping directory="" vcs="Git" /> git表示使用git,svn表示使用svn
