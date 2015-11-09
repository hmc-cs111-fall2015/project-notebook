# Design notebook for week ending November 9, 2014

## Description

###11/2/15

9:45-10:45a

Trying to get the scala files set up.

Everything is almost working, the only problem is adding parsers; I have no clue how to add a jar file.
Or work eclipse at all, basically.

There's using "configure build path" which would be fine and dandy if scala-parser-combinators_2.11-1.0.4.jar was actually in the lib folder for External Piconot and not in Referenced Libraries which isn't accessible!
Fantastic.

_All I had to do was download the .jar file from the internet._

With that being said, perhaps I can find a nice way to add the library I found.

###11/4/15

1:15-2:30p
In-class work time.

Re-downloading the .jar file. Apparently it wasn’t put in the FreeTyle folder (should fix this).

Tile: either freeform or not
freeform tiles do not inherit from normal tiles
has: name, file, optional edge (file)

Since basic tiles can have edges and freeform tiles have anchor points, they’ll be handled too differently to warrant having one extend the other.

An image can be used for either freeform or basic tiles if, for instance, there’s a large object that may be repeated, but also may be scattered along the map (for example, a row of stalagmites across the back of the map, but also some scattered here and there).

Point: has x and y coordinates.

It’s probably going to be useful to have this as an object.

Map: always the same
map has width, height, optional origin (keyword), mutable list of Layers

Layer: has a number to indicate precedence (highest value = topmost layer), mutable list of Areas, mutable list of (FreeTile, Point).

Area: has a tile, mutable list of (Point, Point), each of which specifies a rectangular zone to fill in with the tile
This is what will later be changed for non-rectangular zones.
First iteration: handle just a single rectangle. 
Second iteration: handle multiple rectangles.
Third iteration: handle a list of Points that map out a geometric area.

How to handle second iteration: Make the large rectangle, carve out areas of transparency.

Implement these objects, or at least up to Layers, because the AST will be a list of Layers that will be handled by the semantics to generate the final image.

Then, start focusing on semantics and outputting an image before working on any parsing.

###11/7/15
9:30-10:45a

It seems like it would be easier to work on freeform tile placement first, for the first deliverable.

Now is the time to try, again, to add the IP library (scrimage) using sbt.

I have no idea how to use sbt.

Since this is just layering images and nothing else, I'll just do it myself using the built-in Java stuff(java.awt.image.BufferedImage is a thing).

For now, the background color is set to white.

11:30- 12:30a

Started to implement semantics.scala.

9:00-11:00p

I have no idea if it works, but I have semantics using `java.io.File` and `java.awt`
Time to write a parser to see if it does!

Parsing is going to take more work than expected. It would be best to write a file with the test code first, and then base the parser off of it.

###11/8/15

~2-3 hours

Writing up the design-and-implementation deliverable.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary

## Post-critique reflection
