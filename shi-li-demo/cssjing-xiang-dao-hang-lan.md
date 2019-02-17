# 效果
![](/assets/css实例/css镜像导航栏.gif)

```
<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			html,
			body {
				padding: 0px;
				margin: 0px;
				font-family: 'Raleway', sans-serif;
				color: #FFF;
				height: 100%;
			}
			
			body {
				background: rgba(0, 0, 0, 0.5);
			}
			
			.container {
				max-width: 200px;
				background: rgba(0, 0, 0, 0.75);
				margin: 40px auto;
				padding: 10px 0px 20px 0px;
				border: 1px solid #111;
				border-radius: 4px;
				box-shadow: 0px 4px 5px rgba(0, 0, 0, 0.75);
			}
			
			.link {
				font-size: 16px;
				font-weight: 300;
				text-align: center;
				position: relative;
				height: 40px;
				line-height: 40px;
				margin-top: 10px;
				overflow: hidden;
				width: 90%;
				margin-left: 5%;
				cursor: pointer;
			}
			
			.link:after {
				content: '';
				position: absolute;
				width: 80%;
				border-bottom: 1px solid rgba(255, 255, 255, 0.5);
				bottom: 50%;
				left: -100%;
				transition-delay: all 0.5s;
				transition: all 0.5s;
			}
			
			.link:hover:after,
			.link.hover:after {
				left: 100%;
			}
			
			.link .text {
				text-shadow: 0px -40px 0px rgba(255, 255, 255, 1);
				transition: all 0.75s;
				transform: translateY(100%) translateZ(0);
				transition-delay: all 0.25s;
			}
			
			.link:hover .text,
			.link.hover .text {
				text-shadow: 0px -40px 0px rgba(255, 255, 255, 0);
				transform: translateY(0%) translateZ(0) scale(1.1);
				font-weight: 600;
			}
		</style>
	</head>

	<body>
		<div class="container">
			<div class="link">
				<div class="text">Home</div>
			</div>
			<div class="link">
				<div class="text">Projects</div>
			</div>
			<div class="link">
				<div class="text">Art</div>
			</div>
			<div class="link">
				<div class="text">Social</div>
			</div>
			<div class="link">
				<div class="text">Setup</div>
			</div>
			<div class="link">
				<div class="text">Help</div>
			</div>
		</div>
	</body>

</html>
```

