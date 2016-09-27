# Design notebook for week ending November 16, 2014



## Description

### Interaction

Sometimes when facing a hard question (like how to incorporate custom data into
a language) you need to think about it. While I mulled the prospect over I
decided to implement something else - interactivity!

The pre-function / pre-include version of my language had a REPL which allowed
you to give the interpreter one statement at a time.

Now that I have functions and includes I need to adapt the REPL to work with
them.

I also think it would be nice to add a visual part to the REPL. It would be
cool if the construction you were making appeared as you entered each
statement.

To that end I wrote a [fairly meh] PNG output system, and then looked a bit at
how to get a java swing window to appear with an image that would change as you
entered new statements.


I came back and made the PNG rendered a bit less meh. It labels shapes now in a
semi-reasonable way.

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

The big topics now are data composition and suggestions.

How should suggestions be presented to the user from the Graphic REPL?

How should the user specify new data types?

As inspiration, consider this:

```
data Triangle(Point a, Point b, Point c) =
    Union(Segment(a,b),Segment(b,c),Segment(a,c))
```

I think that the big things you need are the constructor and the rules for
intersection, but I could be missing things.

**What questions do you have for your critique partners? How can they best help
you?**

I think I need some help thinking of natural ways to do the data declarations.

I've also be wondering about moving away from the parenthesis syntax, and
towards something more like natural language. Compare

```
let A = intersection(B, C)
let A be the intersection of B, C
```

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Hmm, maybe 8 hours outside of class. I got the loader/function systems done and
did the renderer?

## Post-critique summary

Robin had a few questions:
   - Why prohibit recursion?
   - What is a locus?
   - What is the space your language does geometry in?
   - What are the tradeoffs associated with dynamic typing?

He also had a few comments:
   - Custom data is nice, think about parrallelograms, etc.
   - Recursion could be good.

## Post-critique reflection

With regards to Robin's questions:
   - I prohibited recursion because it is much tougher than the static function
     implementation I chose. I also think geometry doesn't really use it (at
     least classically).
   - A locus is any set of points. Some are uncountable, some are countable.
   - My language does geometry on R^2.
   - Dynamic typing makes it harder to check for errors without actually doing
     the math. With static typing it might also be cool to make this a 100%
     internal Scala DSL with the Scala type system enforcing types.

With regards to his comments:
   - I agree that custom data is awesome, and I think I need to firm up how the
     users define it. I think constructors are necessary (Robin spoke to this),
     but I also think that some definition of how the type works is required.
     Then again, perhaps these systems can be one and the same. I'll think about
     this more in the coming week.
   - I'm somewhat unsure whether implementing recursion is worth it. If there
     are compelling examples I would definitely do so.
