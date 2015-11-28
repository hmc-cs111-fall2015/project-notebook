# Design notebook for week ending November 30, 2014

## Description

Narrowed down the parsing issue; it can't read the `=' properly.
Added all missing implementation. Found part of the java class that can handle clipping and polygons; this makes it fairly easy to implement the areas.
Debug maps are also implemented. Each layer has a randomized color; may restrict the range to only produce colors that are easily visible.

Filling areas works with:
`fill rectangle (0,0) (1,5) with TILENAME'

or

`fill area (0,0) (4,5) (2,3) with TILENAME'

Rectangles can be specified with two points (the diagonals), three points (the fourth point is inferred), or four points. Areas can be closed, but will automatically be closed if they aren't.

Currently, there is no check for if the 3/4-point specifications are actually rectangular, and a rectangle is fit around whatever area is given.

More error handling is needed, but I'm not certain how to implement it best.

Next is better commenting, which I can do before getting back from break. Later, edges will be implemented.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Parsing is the only thing blocking me from running this thing.

**What questions do you have for your critique partners? How can they best help
you?**

How to parse special characters with packrat parsers, and if I have to give them up, what is the most natural way to specify the filename?
How to do error handling in the IR and semantics?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary

N/A

## Post-critique reflection

N/A
