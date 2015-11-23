# Design notebook for week ending November 23, 2014

## Description

My topic for the upcoming week is types.

### Musing on types

How does the language handle them? How do the users define new types?

I've gotten as far as I have by making the following simplifying assumptions:
   - The user cannot define new types.
   - Constructions take points in and spit points out.

At this point I need to break those assumptions. Constructions should be able
to take and return arbitrary types.

But the interesting question is why do we care? When do we care about the type
of data in our language?

The classic answer is that the type of data specifies which operations can be
performed on it. In some sense we don't care about that here. All of our types
support the same fundamental operations: Intersection, Union, Choosing, etc.

So why do we care about types? Another classic answer is to help catch
programming errors. Realistically we expect certain things to be certain types,
and it is nice to have some way to enforce that.

Consider this block of code:

```
let C = circle(A, B)
```

In this excerpt we expect that `A` and `B` are points (otherwise using the
circle constructor wouldn't make sense).

Another time when we care a lot about types is when we destruct.

Consider

```
let C1 = circle(A, B)
let C2 = circle(B, A)
let D, E = intersection(C1, C2)
```

In this example we assume that the result of the intersection is two things
(which we probably think are points, but we don't make that explicit here).

In some sense we need to be able to determine the type of something in order to
know what it destructs into. Destruction is the fundamental operation that
behaves differently (from a type-system perspective) on different types.

Thus our system for type declaration must provide a users to specify the
components from which shapes are made and what should be done to those
components to generate a Locus which can then be intersected with other loci.
The way to destruct the shape should follow naturally from that - the
interpreter will just have to keep track of what was used to construct the
shape and return that upon destruction.

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.


### Rays and Segments

After doing types I added rays and segments as primatives. This was more work
than one might expect, as increases the number of primative pairings ~ 3fold.

One really awesome part of this was in updating the PNG render to do rays and
line properly (which go off the screen) I needed to figure out the position of
where they left the screen.

If you think about this it is an intersection problem, between the boundary of
the image being drawn and the ray being drawn. I was able to solve it by making
a geometric object for the boundary and intersecting it with the ray :).

This made me feel good about how easy to use the internal geometric engine is!

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Well, I took care of types and the technical debt with missing primitives, so I
guess it is time for search / suggestions?

I think I have 90% of the infrastructure I need to do this, the last thing
might be enforcing input types to functions, that is letting a construction
take something like:

```
given Point A, Point B, Line C
```

Doing this would limit the search space and make suggestions easier.

**What questions do you have for your critique partners? How can they best help
you?**

If you were a user using the GREPL (Graphical REPL), how would you want to ask
for and receive suggestions?

What might a nice syntax for specifying the input types to a construction be?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I never really keep track. Maybe 8 hours out of class.
The extra primitives took a while.

## Post-critique summary

Anna had some valuable ideas. They include

### Syntax

She liked the program-y syntax, although acknowledged her bias as a programmer.

She proposed a pair of data definition syntaxes. One that was inline-ish, one
that was more expansive. What I ended up doing was quite similar to her
expansive version.

In response to her question regarding drawing the intermediaries, I just don't
draw them.

### What are Types? Baby don't hurt me, don't hurt me, no more. ...

Anna was confused about my confusions with types. She notes that a type should
be intersect-able with other types, and perhaps scalable/rotatable?

## Suggestions

She thought that there should be a command for suggestions.

She also thought that this should be filterable by function, by object, perhaps
even by subsets of objects.
I'm super-excited by this suggestion


## Post-critique reflection

### Types

I ended up deciding that types should support everything that the engine's
`Locus` type supports, and also a sort of desctructability - the ability to
recover the things the type was constructed from - it's canonical
representation.

I.E., when I do `Triangle(x,y,z)` I should be able to get `x,y,z` back.

I don't think scaling / rotation are important for classical geometry -
although they sound fun!

### Suggestions

I really appreciated Anna's ideas here, thanks!
