# Design notebook for week ending December 6, 2015

## Description

I spent pretty much all of my time adding support for `if`-`else` statements,
and due to the unexpected increase in complexity,
occasionally reevaluating whether the abstract syntax change was a good idea.
I do still think the conceptual change of a `FlowchartNode`
from "one incoming node, one outgoing node" to "any number of incoming and outgoing nodes"
is good because it actually makes a given flowchart AST easier to understand
since each `FlowchartNode` carries less information.
Probably the most significant detriment to this decision, however,
is that the program that parses a language into the flowchart abstract syntax
likely requires a bit more effort than it would previously,
which sort of adds a barrier to writing a parser to support another language.

Some thoughts on the output flowchart:
I definitely want to work on normalizing the shapes
so that they don't entirely bend to the will of the single-line text they hold.
Specifically, I think they should be more square and have one of a character limit per line,
fixed shape width, or strive for some dimensions (e.g., 4x3).
I think DOT provides support for at least one of these.
I also don't think I'm a fan of the hypotenuse-like arrows; I think I'd prefer corner arrows.
Also for some reason the `true` branches aren't on the same side so I'd like to fix that.
And probably visually distinguish between `if` and `if`-`else` statements.
I also need to look into forcing the flowchart to fit on the page
and start closer to the top.

I think the next bit of progress I'd like to make is to transition the abstract syntax
to Protocol Buffers so that it's less language dependent.
This transition will require separating the visualization from he abstract syntax,
necessitating the creation of separate programs
for parsing the underlying language and generating the graphical flowchart.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Nothin too pressing, though I should add comments to all the code I just wrote.

**What questions do you have for your critique partners? How can they best help
you?**

Comments on my evaluation would be nice.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Probably 8-9. I spent a good hour or so considering whether the new plan is good and will work;
then longer than I'd like to admit implementing.

## Post-critique summary

## Post-critique reflection
