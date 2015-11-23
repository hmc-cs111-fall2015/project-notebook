# Design notebook for week ending November 23, 2014

## Description

X
Spent some time in office hours trying to get a working executable file; will have to wait on that.
Made minimal progress on the parser; it is failing to parse the name of the tiles, for some reason.
I might work on setting up the implementation of everything else in between wrestling with the parser.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary

Robin linked me to some of Alex's code for running from the command line, and also mentioned that I should work on commenting my code.
He also suggested support for hexagons and potentially circles that are part of a larger shape.
Also, links for stress relief things. Excellent.

## Post-critique reflection

With prof Ben's help, I managed to get running from the command line working in Eclipse. At a later point I plan on looking at the suggested code for seeing if this will make things work in the terminal.
The circle suggestion sounds like it would be a freeform tile, though it would be possible to implement circles by calculating the distance between pixels and the center of the circle. The only question there would be if the algorithm would be slowed by it.
As far as hexagons, I have considered other tileable shapes; the two other regular shapes that fill the plane are equilateral triangles and hexagons. This seems like it would probably be a stretch goal.

Though it hasn't come up, I've also thought about how I probably won't get to cutting up the map for ease of use either. Tile sets are still a potential stretch goal.
