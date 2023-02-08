# Random Canvas drawing - Demo/Walkthrough


## I. Start Code

**random-stuff-start.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Random Stuff</title>
	<style>
	canvas{
		border:1px solid gray;
	}
	</style>
	<script>
		"use strict";
		
		//https://en.wikipedia.org/wiki/List_of_Crayola_crayon_colors
		const crayons = ["#ED0A3F","#FF7034","#FFB97B","#FFFF9F","#FFB97B","#33CC99","#00CCCC","#009DC4","#1560BD","#6456B7","#FC74FD","#F7468A","#9E5B40"];
	
		
		const init = () => {
			let canvas = document.querySelector("canvas");
			let ctx = canvas.getContext("2d");
			ctx.fillStyle = "salmon"; 
			ctx.fillRect(20,20,600,440); 

			// circles top-left to bottom-right
			for (let i=0;i<=10;i++){
				ctx.fillStyle = "Yellow"; // try making each one a random crayon color
				ctx.beginPath();
				ctx.arc(i*64,i*48,10,0, Math.PI * 2, false); // vary the radius by a random amount
				ctx.closePath();
				ctx.fill();
				ctx.stroke();
			}
			
			// circles center of screen - large to small radius
			
			
			// wandering line
			
			
			// grid
			
		};
		
		window.onload = init;
	</script>
</head>
<body>
	<canvas width="640" height="480">
		Get a real browser!
	</canvas>
</body>
</html>
```

<hr>

## II. Examples

![screenshot](_images/random-canvas-1.gif)
