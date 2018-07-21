
安装 babel-polyfill
~~~
npm install -save-dev babel-polyfill
~~~

配置
~~~
webpack.base.conf.js文件的
module.exports  的 entry 改为
app: ['babel-polyfill', './src/main.js']

module 下 添加 resolve('static')  把static文件夹下的js也进行转义
{
        test: /\.js$/,
        loader: 'babel-loader',
        include: [resolve('src'), resolve('test'), resolve('static')]
      },
~~~