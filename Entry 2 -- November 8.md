# Design notebook for week ending November 9, 2014

## Description

I've made a lot of progress on the registration and dispatch system (in 
terms of mechanisms - custom data structures are TBI).  At this point it
is theoretically possible to write reactions and use them, however there
are a lot of convenience functions I need to implement.  In particular I
plan on providing a lot of helper functions that analyze whether or not
a molecule is nucleophilic, or is under acidic conditions, etc.  Before I
can do that I need to implement the data structures, and I'll probably 
try to take a first pass at implementing a reaction to get a better idea
of what specifically I'll need to determine in order to predict a reaction.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The first issue will have to be implementing my data structure and figuring out
how much information is necessary to figure out how two molecules will react. I
suspect that my first several attempts will be lacking, but hopefully through an
iterative process I can get it all working.

The next issue will be actually reacting two molecules - this is going to have a 
whole host of problems I haven't even thought up yet, I'm sure.

**What questions do you have for your critique partners? How can they best help
you?**

I'd like to know if my code seems readable, maintainable, and well tested. Right
now a lot of the tests are pretty silly, but I think they're as good as I can get
them until I have a lot of the other stuff fleshed out.

I've also think that I can make my dispatching system more general (it is fairly
general right now) and then the domain specific aspects could be handled by the
users for their own needs - does this seem like it makes sense or that it might
be worthwhile?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Roughly 10 hours - 3ish in class this week, a few more outside of class, and 
then quite a few today (Sunday).

## Post-critique summary

I abstracted most of the Chemistry details away to the point that the reader
could understand the general purpose of the language.  The critiquer was a
little confused by the perceived importance of the dispatch system, and 
thought that the specifics of it probably don't matter as much as the
actual work done in figuring out what works with what.

## Post-critique reflection

I'm very glad to hear that it was general enough to be understandable, and I
hope that I can continue to do that.  I kind of agree that the dispatch system
might not be as tricky as I thought (especially because it ended up being easier
than I had expected), but I think it is still going to be quite important. An
improvement there is an improvement that all mechanisms and reactions will benefit
from, while improving a single mechanism or requirement function will only help
some subset of reactions.
