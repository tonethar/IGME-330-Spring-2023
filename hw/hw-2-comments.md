# HW-2 Comments


## I. App Data Files
- Below are some issues that were seen fairly often 
### I-A. Structure
- #1 - Parallel arrays ... **`:-(`**
  - think about what happens if someone adds a track to the data file - an error is a real possibility
  - data structured like this (in JSON files or in a program) can make you look like a newbie ...
- #2 - Incorrect data types - the strings for `title` and `instructions` are inside of an array - ***why?***

**app-data-that-works-but-structure-needs-work.json**
```json
{
	"title": ["Amazing AudioVisual"],
	"names": ["New Adventure Theme", "Peanuts Theme", "The Picard Song"],
	"urls": ["audio/New Adventure Theme.mp3", "audio/Peanuts Theme.mp3", "audio/The Picard Song.mp3"],
	"instructions": ["Click the play button, and check some boxes to see cool stuff happen."]
}
```

- A better solution groups related data under object literals, and uses strings instead of arrays where appropriate (avoid "array-itus"?)

**app-data-better.json**
```json
{
	"title": "Amazing AudioVisual",
	"tracks": [{
			"track-url": "audio/New Adventure Theme.mp3",
			"track-name": "New Adventure Theme"
		},
		{
			"track-url": "audio/Peanuts Theme.mp3",
			"track-name": "Peanuts Theme"
		},
		{
			"track-url": "audio/The Picard Song.mp3",
			"track-name": "The Picard Song"
		}
	],
	"instructions": "Click the play button, and check some boxes to see cool stuff happen."
}
```

### I-B. Loading the data

- Some of the submissions had page and data loading happening in parallel

**loader.js**
```js

```


- But doing things sequentially makes more sense for this HW

**loader-better.js**
```js

```

<hr>

## II. Sprites

- The requirement was to use ES6 classes, and have at least 2 instances
- If you had more than 2 instances, an array was an appropriate choice:
  - for example, in **canvas.js** rather than having `sprite1`, `sprite2`, ... `sprite5`
  - you should instead have a `sprites` array with 5 sprites in it, and loop through the array to move and draw them
- Sprites should almost always be created ***ONCE*** at app start-up, and then updated (moved/drawn) once a frame
  - some of the submissions were creating new sprite instances ***every frame*** ...
  - ... and adding them to a sprites array ...
  - so after 30 seconds of the AV playing, the sprites array had 5 sprites x 60 PFS x 30 seconds (total: 9000!) sprites in it, which were drawing on top of each otehr

<hr>

## III. Encapsulation

<hr>

## IV. Separation of Concern

<hr><hr>

## XX. Instructor Notes

- Requirements updates:
  - Sprite ES6 classes are contained in a separate file, one class per file
    - example: **phyloFlower.js** contains `class PhylloFlower{ ... }`
    - PS - breaking the file-naming convention for classes is OK - eg. **PhyloFlower.js** is allowed
