

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
				box-sizing: border-box;
			}
			
			h1 {
				color: #37392e;
				font-size: 3.5em;
			}
			
			body {
				background: #F1F4F1;
				font-family: "Roboto Condensed", sans-serif;
				text-align: center;
			}
			
			.o-display-grid {
				display: flex;
				flex-wrap: wrap;
				max-width: 45em;
				margin: 0 auto;
			}
			
			.o-display-grid__item {
				flex-grow: 1;
				flex-basis: 50%;
				text-align: center;
				padding: 1em 2em;
			}
			
			.c-button {
				border: 3px solid #1481ba;
				border-radius: 0;
				color: #1481ba;
				background: #fff;
				text-transform: uppercase;
				font-size: 1em;
				line-height: 1.7em;
				font-weight: bold;
				letter-spacing: .1em;
				font-family: "Roboto Condensed", sans-serif;
				padding: .5em 1.5em;
				cursor: pointer;
				transition: all .5s;
			}
			
			.c-button--box-in {
				box-shadow: inset 0 0 0 0 #1481ba;
			}
			
			.c-button--box-in:hover {
				box-shadow: inset 0 0 0 100vmax #1481ba;
				color: #fff;
			}
			
			.c-button--box-out {
				box-shadow: inset 0 0 0 100vmax #fff, inset 0 0 0 100vmax #1481ba;
			}
			
			.c-button--box-out:hover {
				box-shadow: inset 0 0 0 0 #fff, inset 0 0 0 100vmax #1481ba;
				color: #fff;
			}
			
			.c-button--from-bottom {
				box-shadow: inset 0 0 0 0 #1481ba;
			}
			
			.c-button--from-bottom:hover {
				box-shadow: inset 0 -100vmax 0 0 #1481ba;
				color: #fff;
			}
			
			.c-button--from-top {
				box-shadow: inset 0 0 0 0 #1481ba;
			}
			
			.c-button--from-top:hover {
				box-shadow: inset 0 100vmax 0 0 #1481ba;
				color: #fff;
			}
			
			.c-button--from-left {
				box-shadow: inset 0 0 0 0 #1481ba;
			}
			
			.c-button--from-left:hover {
				box-shadow: inset 100vmax 0 0 0 #1481ba;
				color: #fff;
			}
			
			.c-button--from-right {
				box-shadow: inset 0 0 0 0 #1481ba;
			}
			
			.c-button--from-right:hover {
				box-shadow: inset -100vmax 0 0 0 #1481ba;
				color: #fff;
			}
			
			.c-button--filled {
				background: #1481ba;
				color: #fff;
				box-shadow: inset 0 0 0 0 #fff;
			}
			
			.c-button--filled.c-button--box-in:hover {
				box-shadow: inset 0 0 0 100vmax #fff;
				color: #1481ba;
			}
			
			.c-button--filled.c-button--box-out {
				box-shadow: inset 0 0 0 100vmax #1481ba, inset 0 0 0 100vmax #fff;
			}
			
			.c-button--filled.c-button--box-out:hover {
				box-shadow: inset 0 0 0 0 #1481ba, inset 0 0 0 100vmax #fff;
				color: #1481ba;
			}
			
			.c-button--filled.c-button--from-bottom:hover {
				box-shadow: inset 0 -100vmax 0 0 #fff;
				color: #1481ba;
			}
			
			.c-button--filled.c-button--from-top:hover {
				box-shadow: inset 0 100vmax 0 0 #fff;
				color: #1481ba;
			}
			
			.c-button--filled.c-button--from-left:hover {
				box-shadow: inset 100vmax 0 0 0 #fff;
				color: #1481ba;
			}
			
			.c-button--filled.c-button--from-right:hover {
				box-shadow: inset -15em 0 0 0 #fff;
				color: #1481ba;
			}
			
			.c-button--disabled {
				border-color: #ccc;
			}
			
			.c-button--disabled:hover {
				cursor: not-allowed;
			}
		</style>
	</head>

	<body>
		<h1>CSS Namespaced Button Transitions</h1>
		<div class="o-display-grid">
			<div class="o-display-grid__item">
				<button class="c-button c-button--box-in">Box In</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--box-out">Box Out</button>
			</div>

			<div class="o-display-grid__item">
				<button class="c-button c-button--from-bottom">From Bottom</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--from-top">From Top</button>
			</div>

			<div class="o-display-grid__item">
				<button class="c-button c-button--from-left">From Left</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--from-right">From Right</button>
			</div>

			<div class="o-display-grid__item">
				<button class="c-button c-button--box-in c-button--filled">Filled Box In</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--box-out c-button--filled">Filled Box Out</button>
			</div>

			<div class="o-display-grid__item">
				<button class="c-button c-button--from-bottom c-button--filled">Filled From Bottom</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--from-top c-button--filled">Filled From Top</button>
			</div>

			<div class="o-display-grid__item">
				<button class="c-button c-button--from-left c-button--filled">Filled From Left</button>
			</div>
			<div class="o-display-grid__item">
				<button class="c-button c-button--from-right c-button--filled">Filled From Right</button>
			</div>

		</div>

	</body>

</html>
```

