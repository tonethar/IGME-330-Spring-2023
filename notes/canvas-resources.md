# Canvas & WebAudio Resources

## I. Web Audio Concepts & Notes

- [Web Audio I - Build a Simple Audio Visualizer](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-1.md)
- [Web Audio II - Treble, Bass & Distortion Nodes](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-2.md)
- [Web Audio III - File Chooser](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-3.md)
- [Web Audio IV - Audio Concepts Review](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-4.md)
- [Web Audio V - The WebAudio Convolver Node](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-5.md)
- [Web Audio VI - Bitmap Effects](https://github.com/tonethar/IGME-330-Master/master/notes/demo-web-audio-6.md)

<hr>

## II. WebAudio Book Resources

- [Web Audio Study Guide - Chapter 1 - *Fundamentals*](https://github.com/tonethar/IGME-330-Master/master/notes/web-audio-chapter-1.md)
- [Web Audio Study Guide - Chapter 2 - *Perfect Timing and Latency*](https://github.com/tonethar/IGME-330-Master/master/notes/web-audio-chapter-2.md)
- [Web Audio Study Guide - Chapter 3 - *Volume and Loudness*](https://github.com/tonethar/IGME-330-Master/master/notes/web-audio-chapter-3.md)
- [Web Audio Study Guide - Chapter 4 - *Pitch and the Frequency Domain*](https://github.com/tonethar/IGME-330-Master/master/notes/web-audio-chapter-4.md)

<hr>

## III. Canvas Concepts

<hr>

## IV. Canvas Examples
- [Random Walker](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-random-walker.md)
- [Conway's Life](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-canvas-life.md)
- [Extra Credit - Lorenz Attractor](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-lorenz-attractor.md)
  - generate points over time (using a differential equation), put them in an array, then redraw them all every frame
- ["Nick Cage Clicker" - Canvas Game](https://github.com/tonethar/IGME-330-Master/blob/master/notes/HW-cage-clicker-1.md)

<hr>

## V. Bitmaps

<hr>

## VI. More Demos

- #1 - To get the smoothest canvas animations, and to account for the differing frame rates that [`window.requestAnimationFrame`](https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame) gives you depending on the machine (and monitor) your JS is running on, it's best to calculate a "delta time" to use when drawing animations, and to also consider pausing/unpausing your animations (esp. for a game) when the window goes out of focus:
  - see demos here: https://people.rit.edu/~acjvks/shared/330/canvas/smooth-animation/
  - and also they are zipped up in myCourses
- #2 - DatGUI - Minimalist UI
    - working link is here --> http://igm.rit.edu/~acjvks/courses/shared/330/demos/datGUI-demo/
    - files are in myCourses
