# Design notebook for week ending November 2, 2014

## Description

This week I set a short term goal, and jumped right into making it work as fast
as possible.

The goal was this:

Set up a system in which users could
   1. Get some points
   1. Construct circles and lines around them
   1. Take the intersection of the circles and lines to get even more points
   1. Have the system yell at them if they do something geometrically invalid
   1. ...
   1. Get the results of their construction as an image

I made reasonable progress towards that goal.

### Writing the engine

The end goal for the project is to be able to propose possible actions
that someone might want to take as they make a construction. For this to be
possible the system needs to have some idea of what types of actions are valid
or invalid.

Its also use to be able to detect of certain actions are valid or invalid in
order to validate constructions.

To this end the system needs a geometry engine which can detect whether a
particular action is valid or invalid.

So what are the actions? Classic geometry seems most concerned with actions
like these:
   - Constructing loci from points (constructing circles, lines, segments,
     rays)
   - Finding the intersection of loci - usually result in an enumerable set of
     intersection points (two lines crossing, two circles, etc)
   - Choosing points from loci (from the plane, from a lines)

Constructing loci from points that you've enumerated is always a safe action to
take. However, finding intersections is not always safe. The intersection of a
circle and a lines can be anywhere from 0 to 2 points. We need an engine to
determine how many intersection points there are.

The question of choosing points is also an interesting one, but not one that I
thought much about. When we choose a point on a line not just any point will
do. I think there are some implicit preferences.

At any rate, I wrote an engine which allowed circles and lines to be
constructed from points, and for the intersections of circles and lines to be
computed resulting in more enumerated points.

One of the interesting questions this raised is how to deal with enumerable and
non-enumerable sets of points. In geometry you have need for both. Should they
be separate types or the same type? Things to think about...

One of the decisions I made during this segment of work was that a locus of
points is an object which can be intersected with other loci to produce an
enumerable set of points. This seems like a useful model, but other could exist
as well. In fact, it's not even accurate. Intersecting a line with itself
results in the same line, the points of which cannot be enumerated.

To the critic - what are your thoughts on this model? What are the fundamental
types of geometry?

### The parser & interpreter

I also wrote a parser and interpreter which interfaced between the user and the
engine. I chose to make the syntax pretty verbose. A program looks something
like:

```
let A be a point;
let B be a point;
let C1 be a circle with center A and edge B;
let C2 be a circle with center B and edge A;
let C1 and C2 intersect at D, E;
let p be a line from D to E;
let q be a line from A to B;
let p and q intersect at O;
```

this computes the midpoint of two other points.

The parser parses the above syntax into an Abstract Syntax Tree and the
interpreter interprets the construction one line at a time checking for
geometric validity.

I chose to keep the syntax very verbose because I liked the similarity to
mathematical writing. That being said, it does take a long time to write -
I'll probably take another pass at it later.

### The TkzEuclide output tool

I also wrote a system to output a geometric construction from the interpreter
into the syntax of the LaTeX package `tkz-euclide`. This didn't go quite as
smoothly as I expected, but it did work. I think I need to define another sort
of AST that the interpreter / engine can produce which allows a generic
rendering system to easily render an image. The specific problem I ran into
this time around was that circles contained the coordinates of the points they
were constructed from, but not the names of those points. Since tkz-euclide
uses the names of these input points rather than their location, doing the
rendering was a bit more challenging.

I think that trying to design some sort of super-redundant output AST for the
construction would make writing different rendering systems much easier, even
if those rendering systems are targeted at different final formats and use
different packages / libraries to do the rendering.

### The 'compiler' and REPL

Finally, I put together all the pieces into a whole-file interpreter (called
the compiler) which reads a file, parses it, interprets it, and outputs LaTeX
source which uses tkz-euclide to render the construction.

The REPL loop takes one statement at a time and interprets them to build a
construction. At each step it dumps a (not so useful) list of the current loci
and points which have been defined.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I see three pressing issue right now:

The first is that I need to get a grip on the fundamental types of the
language, as well as the fundamental operations that they should support.

My current vision is this:
The fundamental types are *points* and *loci*. Points can be composed using
Haskel-style data constructors to make loci. Loci can be intersected with each
other to get enumerable sets of points.

Users can define new data constructors (which can be build from points and/or
loci) that build new subtype of loci and define rules for how they intercept
with other loci.

Users can also define new procedures which take some points/loci and output
some other points/loci.

However, I could also imagine a model in which the point and loci types are
unified into a single point-set type.

To the critic - do you think that points and loci should be unified? Advantages
and drawbacks?

The second issue is how this composition (data constructor and/or subroutines)
should work. I think that this issue will be fairly naturally resolved when I
have a firm grip on what the fundamental types are.

The third issue is how I should clarify the three parts of this project, the
user interface, the intermediate layer, and the rendering system.

Ideally I would like to spend the majority of this project working on the
intermediate layer - the layer that lives exclusively inside Scala and provides
an interface to do constructions, to search possible actions, and to get a dump
of the current construction for outputting. I need to pin down exactly what the
interface provided by this intermediate layer should be. How should the user
interface (text or visual) interact with it? How should the rendering system
interact with it?

**What questions do you have for your critique partners? How can they best help
you?**

I would love to hear any thoughts you have regarding the fundamental types
(point & locus vs point-set) and I would also be curious how you think I
should divide responsibility between the 3 layers of my project.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I didn't really keep track to be honest, I just worked whenever I could.
I would guess somewhere around ~12 hours.

## Post-critique summary

## Post-critique reflection
