<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			html {
				height: 100%;
			}
			
			body {
				background: #6FA5F6;
				width: 100%;
				height: 100%;
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
			
			.password {
				width: 350px;
				height: 75px;
				background: #121727;
				border-radius: 10px;
				position: relative;
				overflow: hidden;
				-webkit-box-shadow: 0 0 12px 0px rgba(1, 1, 1, 0.25);
				box-shadow: 0 0 12px 0px rgba(1, 1, 1, 0.25);
			}
			
			.password--background {
				background: #FEFEFE;
				position: absolute;
				width: 150%;
				height: 100%;
				right: -50%;
				top: 0;
				-webkit-transition: .20s all ease-in-out;
				transition: .20s all ease-in-out;
				border-radius: 5px;
			}
			
			.password--visibleToggle {
				position: absolute;
				width: 50px;
				height: 50px;
				right: 10px;
				top: 10px;
				z-index: 1;
				-webkit-appearance: none;
				-moz-appearance: none;
				appearance: none;
				outline: none;
			}
			
			.password--visibleToggle-eye {
				width: 25px;
				height: 25px;
				position: absolute;
				right: 25px;
				top: 25px;
				-webkit-perspective: 1000px;
				perspective: 1000px;
				overflow: hidden;
			}
			
			.password--visibleToggle-eye.close {
				-webkit-transition: .4s all ease-in-out;
				transition: .4s all ease-in-out;
			}
			
			.password--visibleToggle-eye.open {
				-webkit-transition: .2s .2s all ease-out;
				transition: .2s .2s all ease-out;
			}
			
			.password--visibleToggle-eye img {
				width: 100%;
			}
			
			.password--lock {
				width: 20px;
				height: 20px;
				fill: #111;
				-webkit-transition: all .5s;
				transition: all .5s;
				position: absolute;
				top: 50%;
				-webkit-transform: translateY(-50%);
				transform: translateY(-50%);
				left: 25px;
			}
			
			.password--input {
				background: none;
				border: none;
				color: #575DBF;
				position: absolute;
				width: 200px;
				left: 60px;
				top: 50%;
				-webkit-transform: translateY(-50%);
				transform: translateY(-50%);
				font-size: 18px;
				letter-spacing: 2px;
				-webkit-transition: all .5s;
				transition: all .5s;
				outline: none;
				font-family: 'Open Sans Condensed', sans-serif;
				-webkit-text-security: none;
			}
			
			.password--input:focus {
				border-bottom: 1px solid;
			}
			
			.password--visibleToggle:checked~.password--background {
				width: 50px;
				height: 50px;
				border-radius: 50%;
				right: 12.5px;
				top: 12.5px;
			}
			
			.password--visibleToggle:checked~.password--input {
				-webkit-text-security: circle;
			}
			
			.password--visibleToggle:checked~.password--lock {
				fill: #fff;
			}
			
			.password--visibleToggle:checked~.password--visibleToggle-eye.close {
				-webkit-transform: rotateX(180deg);
				transform: rotateX(180deg);
			}
			
			.password--visibleToggle:checked~.password--visibleToggle-eye.open {
				opacity: 0;
			}
		</style>
	</head>

	<body>
		<div class="password">
			<input type="checkbox" class="password--visibleToggle" checked>
			<div class="password--background"></div>
			<div class="password--visibleToggle-eye open">
				<img src="http://jq22.qiniudn.com/eye-open.png" />
			</div>
			<div class="password--visibleToggle-eye close">
				<img src="http://jq22.qiniudn.com/eye-close.png" />
			</div>
			<svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 30.221 30.221" style="enable-background:new 0 0 30.221 30.221;" xml:space="preserve" class="password--lock">
				<g>
					<path d="M25.534,14.457h-1.529V9.361c0-2.541-0.965-4.871-2.555-6.572C19.864,1.09,17.602-0.006,15.11,0
		c-2.494-0.006-4.756,1.09-6.34,2.789C7.179,4.49,6.214,6.82,6.214,9.361v5.096H4.683c-0.629,0-1.145,0.512-1.145,1.145v13.471
		c0,0.637,0.516,1.148,1.145,1.148h20.852c0.635,0,1.148-0.512,1.148-1.148V15.602C26.683,14.969,26.169,14.457,25.534,14.457z
		 M10.436,9.361c0-1.465,0.559-2.766,1.42-3.686c0.867-0.922,2-1.453,3.254-1.453c1.252,0,2.385,0.531,3.25,1.453
		c0.865,0.92,1.42,2.221,1.42,3.686v5.096h-9.344V9.361z" />
				</g>
			</svg>
			<input type="text" class="password--input" value="madewithlove" />
		</div>

	</body>

</html>