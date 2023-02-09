# Random Canvas drawing - Demo/Walkthrough

- Video walkthrough link -> [Random Canvas - Loops and Animation(19:21)](https://rit.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=d0c5c788-92e0-4328-badb-afa4000665d0)

<hr> 

## I. Genuary 
- https://genuary.art/
  - "GENUARY is an artificially generated month of time where we build code that makes beautiful things."
- "Made in 10 Minutes" prompt
  - https://app.joyn.xyz/contest/genuary-day-gallery-made-in-minutes-cae91e45aed8
  - I suspect most of these submissions took longer than 10 minutes
  - I made the done version below in around 30-40 minutes ...
  - which is pretty good when using canvas because we don't have all the built-in functions that [p5.js](https://p5js.org/) has for 3D primitives, perlin noise etc

<hr>

## II. Generative Art & Randomness
- [Randomness and Aesthetics Notes](./randomness.md)
- For this exercise, we'll use loops, "primitive" canvas shapes and animation to create some simple generative art
- PS - Next week we'll look other generative art techniques - that don't use randomness - for example "Phyllotaxis - Procedural Flower generation"

<hr>

## III. Start Code

**random-stuff-start.html**

```html
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8" />
	<title>Random Canvas Stuff</title>
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

## IV. Examples

![screenshot](_images/random-canvas-1.gif)
