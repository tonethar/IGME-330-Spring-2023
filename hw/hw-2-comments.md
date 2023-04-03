# HW-2 Comments


## I. App Data Files
### I-A. Structure
- Parallel arrays **:-(**
  - think about what happens if someone adds a track to the data file - an error is a real possibility
- Incorrect data types - the `title` and `instructions` are an array - ***why?***
- Something like this was seen fairly often (note also 

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

```

### I-B. Loading


<hr>

## II. Sprites


<hr>

## XX. Instructor Notes
