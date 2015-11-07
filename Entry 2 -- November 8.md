# Design notebook for week ending November 9, 2014

Also known as "The week of type systems"

## Description

### On the type system

Until now I've been thinking of the type system as having 3 things:
   - A concrete Point
   - An uncountably infinite Locus of points
   - An enumerable Set of points

And I've been using a model with the following operations:
   - Locus intersect Locus -> Set
   - Constructor [Point] -> Locus
   - Destruct Set -> [Point]
   - Locus choose -> Point

This is somewhat nice, because when you intersect Loci you get points, and then
you know that you can take those points and build Loci from them using
constructors.

But there's a dirty secret. `Locus intersect Locus -> Set` is a lie. Consider a
line intersecting with itself. The result is the original line, which is not an
enumerable set.

This is a deep problem. The way I've tackled it for now is by pushing a lot of
the type-checking to runtime.

The new type model is this:

```
Locus:
    Single:
        Primative:
            Line
            Circle
            Ray
            Segment
        Point
    Union
```

Where the following operations exist:

```
Locus intersect Locus -> Locus
Locus union     Locus -> Locus
Locus choose          -> Option[Point]
```

The problem remains of how to construct Loci. I think we'll just have to have
convenience constructors which take Loci and check their types before using the
case class constructors.

One point of reflection is that I'm taking my language very much in the direct
of a static type system. Coming from a language like Rust this makes me sad,
because Rust uses it static type system[s] to great effect. However, I feel
okay with the change because it was motivated by geometric facts - the idea
that the intersections of uncountable loci do not always result in points.

### On Functions and the Geometry Engine as an Internal DSL

I've started to turn my thoughts more towards functions as of late.

As a brief reminder, I very much want users of my language to be able to easily
reuse their constructions. It seems to me that in reusing a construction one
starts with some set of points [and/or loci?], performs some actions, and then
returns some points and or loci as a result of those actions.

So can we provide this experience to the user, and what does this have to do
with the geometry engine as a DSL living inside Scala?

Well, if we make the geometry engine a Scala DSL, then it seems natural to have
our functions be Scala functions, and to have our external DSL compile to Scala
in a way which maps the functions the user writes to Scala functions.

This is a bit of a daunting prospect, but it could be done. The larger concern
is how this would interact with the suggestion system.

For background one of the goals of my project was to allow for suggestions to
be made to a user who was interactively writing a program. Hopefully this
system would be extensible enough to allow those suggestions to use the
procedures which the user had defined as well as build in ones.

For this to be possible user procedures would have to be indexable and
interpretable by a running program, which seems somewhat challenging if they
are being compiled into Scala functions.

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

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
