
```
<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			html {
				box-sizing: border-box;
				font-family: "Nothing You Could Do";
			}
			
			*,
			*:before,
			*:after {
				box-sizing: inherit;
			}
			
			html,
			body {
				height: 100%;
			}
			
			body {
				background-color: #F1F1F1;
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-pack: center;
				-ms-flex-pack: center;
				justify-content: center;
				-webkit-box-align: center;
				-ms-flex-align: center;
				align-items: center;
			}
			
			.heading {
				position: fixed;
				bottom: 0;
				right: 0;
				margin: 2vmin 3vmin;
				color: #999;
			}
			
			.card-container {
				position: relative;
				width: 65vmin;
				height: 80vmin;
			}
			
			.card {
				position: absolute;
				top: 0;
				left: 0;
				width: 100%;
				height: 100%;
				background-color: #fafafa;
				border-radius: 2px;
				box-shadow: 2px 2px 5px rgba(17, 17, 17, 0.35);
				-webkit-transition: -webkit-transform .35s ease-out;
				transition: -webkit-transform .35s ease-out;
				transition: transform .35s ease-out;
				transition: transform .35s ease-out, -webkit-transform .35s ease-out;
				-webkit-transform: translate(var(--x), var(--y)) scale(0.35) rotate(var(--angle));
				transform: translate(var(--x), var(--y)) scale(0.35) rotate(var(--angle));
				will-change: transform;
			}
			
			.card:hover {
				-webkit-transform: scale(1) rotate(0deg);
				transform: scale(1) rotate(0deg);
				z-index: 1;
			}
			
			.card:hover:before {
				opacity: 1;
			}
			
			.card:before {
				content: "";
				display: block;
				width: 90%;
				height: 80%;
				margin: 5%;
				background: var(--image) center center no-repeat;
				background-size: cover;
				box-shadow: inset 0 0 5px rgba(34, 34, 34, 0.35);
				border-radius: 2px;
				-webkit-filter: sepia(0.2) brightness(0.9) contrast(1.2);
				filter: sepia(0.2) brightness(0.9) contrast(1.2);
				-webkit-transition: opacity .35s ease-out;
				transition: opacity .35s ease-out;
				opacity: .5;
				will-change: opacity;
			}
			
			.card:after {
				display: block;
				content: var(--caption);
				font-weight: 500;
				color: #555;
				font-size: 3vmin;
				opacity: .75;
				text-align: center;
			}
		</style>
	</head>

	<body>
		<h1 class="heading">Polaroid Memories</h1>

		<div class="card-container">
			<div class="card" style="--image: url('http://www.jq22.com/demo/jqueryCorner201709040902/images/01.png'); --angle: -5deg; --x: 5%; --y: 15%; --caption: 'Berlin in 2009'"></div>
			<div class="card" style="--image: url('http://www.jq22.com/demo/jqueryCorner201709040902/images/02.png'); --angle: -1deg; --x: -10%; --y: -20%; --caption: 'London, 2001'"></div>
			<div class="card" style="--image: url('http://www.jq22.com/demo/jqueryCorner201709040902/images/03.png'); --angle: -4deg; --x: -20%; --y: 5%; --caption: 'Los Angeles - 2004'"></div>

		</div>

	</body>

</html>
```

