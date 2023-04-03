# HW-2 Comments


## I. App Data Files
- Below are some issues that were seen fairly often 
### I-A. Structure
- #1 - Parallel arrays ... **`:-(`**
  - think about what happens if someone adds a track to the data file - an error is a real possibility
  - data like this cam make you look like a newbie ...
- #2 - Incorrect data types - the `title` and `instructions` are an array - ***why?***


```json
{
	"title": ["Amazing AudioVisual"],
	"names": ["New Adventure Theme", "Peanuts Theme", "The Picard Song"],
	"urls": ["audio/New Adventure Theme.mp3", "audio/Peanuts Theme.mp3", "audio/The Picard Song.mp3"],
	"instructions": ["Click the play button, and check some boxes to see cool stuff happen."]
}
```

- A better solution groups related data under object literals, and uses a string instead of an array (so don't get "array-itus"?)

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

### I-B. Loading


<hr>

## II. Sprites


<hr>

## XX. Instructor Notes
