# 效果
![](/assets/css实例/纯css3从中间显示下划线动画导航菜单.gif)

```
<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			* {
				margin: 0;
				padding: 0;
			}
			
			li,
			a {
				text-decoration: none;
				list-style: none;
				color: #484848
			}
			
			.nav {
				width: 1000px;
				height: 50px;
				border: 1px solid #ccc;
				margin: 0 auto;
				line-height: 50px;
				margin-top: 50px;
			}
			/*-----------------------导航1111111111-----------------------------*/
			
			.nav1 a {
				width: 70px;
				height: 100%;
				float: left;
				margin: 0 15px;
				position: relative;
				text-align: center;
			}
			
			.nav1 a span {
				margin: auto;
				display: inline-block;
				position: absolute;
				bottom: 5px;
				left: 0;
				right: 0;
				width: 0px;
				height: 2px;
				background: #ff0000;
				transition: .5s;
				border-radius: 50px;
			}
			
			.nav1 a:hover span {
				width: 100%;
				left: 0;
			}
			/*-----------------------导航2222222-----------------------------*/
			
			.nav2 a {
				width: 70px;
				height: 100%;
				float: left;
				margin: 0 15px;
				position: relative;
				text-align: center;
			}
			
			.nav2 a span {
				margin: auto;
				display: inline-block;
				position: absolute;
				bottom: 5px;
				left: 0;
				width: 0px;
				height: 2px;
				background: #ff0000;
				transition: .5s;
				border-radius: 50px;
			}
			
			.nav2 a:hover span {
				width: 100%;
			}
		</style>
	</head>

	<body>
		<div class="nav nav1">
			<li>
				<a href="javascript:void(0)">导航1
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航2
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航3
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航4
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航5
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航6
					<span></span>
				</a>
			</li>
		</div>

		<div class="nav nav2">
			<li>
				<a href="javascript:void(0)">导航1
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航2
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航3
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航4
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航5
					<span></span>
				</a>
			</li>
			<li>
				<a href="javascript:void(0)">导航6
					<span></span>
				</a>
			</li>
		</div>
	</body>

</html>
```

