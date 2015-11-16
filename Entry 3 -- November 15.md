# Design notebook for week ending November 16, 2014

## Description

The first thing I did this week was integrate documentation more completely into
the project - you can now view the documentation all nice and pretty, hosted online
at [readthedocs.org][1].

After that I spent some time integrating the method of registering structures with
the dispatch system, as well as implementing the generic structure itself.  As of the
time of writing I haven't completed integrating them - I have a few design decisions I
need to make, and I think I want to redo some of how I did things before - for example 
I don't want `__call__` to be the decorator, but rather I think I want two classmethods
that I can use to register mechanisms and structures.  This would mesh better with what
the class is and how it should be used.

I also need to think more about how to implement the structure - right now I have a
pretty generic class that 

  a) needs more testing, and  
  b) doesn't really do anything
  
I think adding to this structure might have to wait until I've added a reaction mechanism
and some requirements functions to the mix and I have a better idea of what they require.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

How to best represent a molecule.

**What questions do you have for your critique partners? How can they best help
you?**

Since I didn't get critiqued this week, I'd appreciate the same feedback as last week,
with the additional feedback on how good the documentation is.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

10 hours or so

## Post-critique summary

No critique received.

## Post-critique reflection

No critique received.



  [1]: http://caos.rtfd.org/en/latest/
