

```
<!doctype html>
<html>

	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
		<meta http-equiv="X-UA-Compatible" content="ie=edge">
		<title>Document</title>
		<style>
			body {
				font-size: 20px;
				font-family: system-ui, Helvetica, Arial, sans-serif;
				background: #fff;
			}
			
			form {
				width: 300px;
				margin: 20px auto;
			}
			
			fieldset {
				position: relative;
				border: none;
			}
			
			label {
				position: absolute;
				top: 18px;
				color: rgba(0, 0, 0, 0.3);
				transform-origin: left;
				transition: all 0.3s ease;
			}
			
			input:focus~label {
				color: red;
			}
			
			input:focus~label,
			input:valid~label {
				top: 0;
				transform: scale(0.6, 0.6);
			}
			
			input {
				font-size: 20px;
				width: 100%;
				border: none;
				margin-top: 10px;
			}
			
			input:focus {
				outline: none;
			}
			
			.after {
				width: 100%;
				height: 2px;
				background: linear-gradient(to right, red 50%, transparent 50%);
				background-color: rgba(0, 0, 0, 0.3);
				background-size: 200% 100%;
				background-position: 100% 0;
				transition: all 0.6s ease;
			}
			
			input:focus~.after {
				background-position: 0 0;
			}
			
			button {
				position: relative;
				width: 100%;
				font-size: 20px;
				font-family: system-ui, Helvetica, Arial, sans-serif;
				line-height: 1.5;
				margin-top: 20px;
				padding: 2px 10px;
				color: rgba(0, 0, 0, 0.4);
				background: white;
				border: none;
				background: linear-gradient(to right, red 50%, transparent 50%);
				background-color: rgba(0, 0, 0, 0.3);
				background-size: 200% 100%;
				background-position: 100% 0;
				transition: all 0.6s ease;
			}
			
			button:before {
				position: absolute;
				content: "Submit";
				top: 2px;
				bottom: 2px;
				left: 2px;
				right: 2px;
				display: block;
				background-color: white;
			}
			
			button:active,
			button:focus,
			button:hover {
				outline: none;
				background-position: 0 0;
				color: red;
			}
		</style>
	</head>

	<body>
		<fieldset>
			<input id="first" type="text" name="first" required>
			<label for="first">First Name</label>
			<div class="after"></div>
		</fieldset>
		<fieldset>
			<input id="last" type="text" name="last" required>
			<label for="last">Last Name</label>
			<div class="after"></div>
		</fieldset>
		<fieldset>
			<button>Submit</button>
		</fieldset>

	</body>

</html>
```

