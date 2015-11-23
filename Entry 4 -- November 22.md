# Design notebook for week ending November 23, 2014

## Description

Alright, I've finally decided to abandon trying for an internal DSL.
Since I wanted to be able to write arbitrary code,
this is a significant change.
But I just haven't been quite able to wrangle Scala or Python to do what I want.
In particular, I'd like to be able to edit Scala classes I've already made,
in ways more powerful than I think implicits can do,
but I don't think that plays very nicely with types. :)

So it'll be an external DSL, with Python in the backend.
Check out `prototype/example.txt` for what the syntax will look like.

Notably, this basically just constructs classes for AST nodes.
There's no way to actually use those nodes yet!

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I believe that I can implement what is shown in `example.txt`. What that leaves is,
how useful is that actually?
What can I do with it?
And, is it even useable/understandable as is?

**What questions do you have for your critique partners? How can they best help
you?**

I want to know if `example.txt` makes any sense.
Just the top half, really.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Most of the time I spent was again on implementation and therefore opaque.
Overall, 7 hours.
Syntax proposal was 2.


## Post-critique summary

## Post-critique reflection
