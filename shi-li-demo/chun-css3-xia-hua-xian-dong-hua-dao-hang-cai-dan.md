<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
	</head>

	<body>
		<ul class="a">
			<li class="n1">
				<a href="#">Navigator A</a>
			</li>
			<li class="n2">
				<a href="#">Navigator B</a>
			</li>
			<li class="n3 selected">
				<a href="#">Navigator C</a>
			</li>
			<li class="n4">
				<a href="#">Navigator D</a>
			</li>
			<li class="quebec">&nbsp;</li>
		</ul>
		<style>
			ul {
				position: relative;
				overflow: hidden;
				padding-left: 0px;
			}
			
			li {
				list-style: none outside;
				position: relative;
				z-index: 1;
				float: left;
				padding: 0 0 0 0;
				margin-right: 10px;
			}
			
			li a {
				position: relative;
				width: 100px;
				color: #333;
				display: block;
				margin: 0 0;
				border-bottom: 5px solid transparent;
				padding: 10px 0;
				text-align: center;
				text-decoration: none;
			}
			
			.selected a {
				border-bottom: 5px solid #cfd0d0;
				color: #511d7f;
			}
			
			.quebec {
				position: absolute;
				bottom: 0px;
				left: -100px;
				z-index: 3;
				margin: 0;
				border: 0;
				width: 5px;
				height: 5px;
				padding: 0;
				overflow: hidden;
				background: #511d7f;
				-webkit-transition-property: left, width;
				-moz-transition-property: left, width;
				-ms-transition-property: left, width;
				-o-transition-property: left, width;
				transition-property: left, width;
				-webkit-transition-duration: .5s;
				-moz-transition-duration: .5s;
				-ms-transition-duration: .5s;
				-o-transition-duration: .5s;
				transition-duration: .5s;
			}
			
			.n1:hover~li.quebec {
				left: 5px;
				width: 110px;
			}
			
			.n2:hover~li.quebec {
				left: 115px;
				width: 110px;
			}
			
			.n3:hover~li.quebec {
				left: 225px;
				width: 110px;
			}
			
			.n4:hover~li.quebec {
				left: 335px;
				width: 110px;
			}
		</style>
	</body>

</html>