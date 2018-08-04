

```
<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			/*
 * demo styles
 */
			
			@media screen and (min-width: 769px) {
				html {
					font-size: 62.5%;
				}
			}
			
			@media screen and (min-width: 641px) and (max-width: 768px) {
				html {
					font-size: 56%;
				}
			}
			
			@media screen and (max-width: 640px) {
				html {
					font-size: 50%;
				}
			}
			
			body {
				font-family: "PT Sans", -apple-system, BlinkMacSystemFont, "Roboto", "Open Sans", "Helvetica Neue", "Segoe UI", "Arial", sans-serif;
				font-size: 1.6rem;
				margin: 0;
				-webkit-overflow-scrolling: touch;
				background-color: #f0f0f0;
			}
			
			a {
				color: inherit
			}
			
			.page {
				height: 100vh;
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-orient: vertical;
				-webkit-box-direction: normal;
				-ms-flex-direction: column;
				flex-direction: column;
				-ms-flex-pack: distribute;
				justify-content: space-around;
			}
			
			@media screen and (min-width: 1200px) {
				.page {
					height: 100vh;
				}
			}
			
			@media screen and (max-width: 1199px) {
				.page {
					min-height: 100vh;
				}
			}
			
			.demo {
				-webkit-box-flex: 2;
				-ms-flex-positive: 2;
				flex-grow: 2;
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-align: center;
				-ms-flex-align: center;
				align-items: center;
				-webkit-box-pack: center;
				-ms-flex-pack: center;
				justify-content: center;
			}
			
			.main-container {
				width: 100%;
				max-width: 1300px;
				padding: 1rem;
				box-sizing: border-box;
			}
			
			.buttons {
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
			}
			
			@media screen and (max-width: 1199px) {
				.buttons {
					-webkit-box-orient: vertical;
					-webkit-box-direction: normal;
					-ms-flex-direction: column;
					flex-direction: column;
					-ms-flex-wrap: wrap;
					flex-wrap: wrap;
					-webkit-box-align: center;
					-ms-flex-align: center;
					align-items: center;
					-webkit-box-pack: start;
					-ms-flex-pack: start;
					justify-content: flex-start;
				}
				.button {
					margin-top: 3%;
				}
				.button:first-child {
					margin-top: 0;
				}
			}
			
			@media screen and (min-width: 1200px) {
				.button {
					width: 24%;
				}
				.button:nth-child(4n+2) {
					margin-right: .6666%;
					margin-left: 1.3333%
				}
				.button:nth-child(4n+3) {
					margin-right: 1.3333%;
					margin-left: .6666%;
				}
			}
			
			.button__hint {
				font-size: 1.4rem;
				display: block;
				text-align: center;
			}
			
			.footer {
				background-color: #673AB7;
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-pack: center;
				-ms-flex-pack: center;
				justify-content: center;
				color: #fff;
			}
			
			@media screen and (max-width: 640px) {
				.footer {
					font-size: 1.4rem;
				}
			}
			
			.footer__container {
				display: -webkit-box;
				display: -ms-flexbox;
				display: flex;
				-webkit-box-pack: center;
				-ms-flex-pack: center;
				justify-content: center;
			}
			/*
 * button
 */
			
			.button {
				cursor: pointer;
				padding: .8em 2em;
				box-sizing: border-box;
				position: relative;
				overflow: hidden;
				font-family: inherit;
				font-size: 1.8rem;
				color: #fff;
				text-transform: uppercase;
				letter-spacing: .5px;
				outline: none;
				border: none;
				background-color: #512DA8;
				border-radius: 5px;
			}
			
			.button:before {
				content: "";
				background-color: #448AFF;
				position: absolute;
			}
			
			.button__label {
				position: relative;
				z-index: 2;
			}
			/* effect 1 */
			
			.button_type1:before {
				width: 200%;
				height: 150%;
				opacity: 0;
				left: -50%;
				bottom: 0;
				-webkit-transform-origin: left bottom;
				transform-origin: left bottom;
				-webkit-transform: rotate(-90deg) translateZ(0);
				transform: rotate(-90deg) translateZ(0);
				-webkit-transition: opacity 3s cubic-bezier(0.01, -0.24, 0, 0.68), -webkit-transform 3s cubic-bezier(0.01, -0.24, 0, 0.68);
				transition: opacity 3s cubic-bezier(0.01, -0.24, 0, 0.68), -webkit-transform 3s cubic-bezier(0.01, -0.24, 0, 0.68);
				transition: transform 3s cubic-bezier(0.01, -0.24, 0, 0.68), opacity 3s cubic-bezier(0.01, -0.24, 0, 0.68);
				transition: transform 3s cubic-bezier(0.01, -0.24, 0, 0.68), opacity 3s cubic-bezier(0.01, -0.24, 0, 0.68), -webkit-transform 3s cubic-bezier(0.01, -0.24, 0, 0.68);
			}
			
			.button_type1:hover:before,
			.button_type1:focus:before {
				-webkit-transform: rotate(0deg) translateZ(0);
				transform: rotate(0deg) translateZ(0);
				opacity: 1;
				-webkit-transition-duration: .6s, .6s;
				transition-duration: .6s, .6s;
			}
			/* effect 2 */
			
			.button_type2:before {
				width: 0;
				height: 0;
				padding: 18%;
				border-radius: 50%;
				left: 50%;
				top: 50%;
				-webkit-transform: translate3d(-50%, -50%, 0) scale(0);
				transform: translate3d(-50%, -50%, 0) scale(0);
				-webkit-transition: -webkit-transform .3s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: -webkit-transform .3s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform .3s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform .3s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform .3s cubic-bezier(1, 0.15, 0.34, 1.03);
			}
			
			.button_type2:hover:before,
			.button_type2:focus:before {
				-webkit-transform: translate3d(-50%, -50%, 0) scale(2.5);
				transform: translate3d(-50%, -50%, 0) scale(2.5);
			}
			/* effect 3 */
			
			.button_type3:before {
				width: 200%;
				height: 25%;
				opacity: 0;
				left: 50%;
				top: 50%;
				-webkit-transform: translate3d(-50%, -50%, 0) scale(.1);
				transform: translate3d(-50%, -50%, 0) scale(.1);
				-webkit-transition: opacity .3s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform .7s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: opacity .3s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform .7s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform .7s cubic-bezier(1, 0.15, 0.34, 1.03), opacity .3s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform .7s cubic-bezier(1, 0.15, 0.34, 1.03), opacity .3s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform .7s cubic-bezier(1, 0.15, 0.34, 1.03);
			}
			
			.button_type3:hover:before,
			.button_type3:focus:before {
				opacity: 1;
				-webkit-transform: translate3d(-50%, -50%, 0) scale(5);
				transform: translate3d(-50%, -50%, 0) scale(5);
			}
			/* effect 4 */
			
			.button_type4:before {
				width: 20%;
				height: 200%;
				opacity: 0;
				left: 50%;
				top: 50%;
				-webkit-transform: translate3d(-50%, -50%, 0) scale(.1);
				transform: translate3d(-50%, -50%, 0) scale(.1);
				-webkit-transition: opacity .2s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform 1s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: opacity .2s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform 1s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform 1s cubic-bezier(1, 0.15, 0.34, 1.03), opacity .2s cubic-bezier(1, 0.15, 0.34, 1.03);
				transition: transform 1s cubic-bezier(1, 0.15, 0.34, 1.03), opacity .2s cubic-bezier(1, 0.15, 0.34, 1.03), -webkit-transform 1s cubic-bezier(1, 0.15, 0.34, 1.03);
			}
			
			.button_type4:hover:before,
			.button_type4:focus:before {
				opacity: 1;
				-webkit-transition-duration: .7s, .3s;
				transition-duration: .7s, .3s;
				-webkit-transform: translate3d(-50%, -50%, 0) scale(5);
				transform: translate3d(-50%, -50%, 0) scale(5);
			}
		</style>
	</head>

	<body>
		<div class="page">
			<div class="demo">
				<div class="main-container">
					<div class="buttons">
						<button class="button button_type1">
          <span class="button__label">Press on me</span>
          <span class="button__label button__hint">effect 1</span>
        </button>
						<button class="button button_type2">
          <span class="button__label">Press on me</span>
          <span class="button__label button__hint">effect 2</span>
        </button>
						<button class="button button_type3">
          <span class="button__label">Press on me</span>
          <span class="button__label button__hint">effect 3</span>
        </button>
						<button class="button button_type4">
          <span class="button__label">Press on me</span>
          <span class="button__label button__hint">effect 4</span>
        </button>
					</div>
				</div>
			</div>
		</div>

	</body>

</html>
```

