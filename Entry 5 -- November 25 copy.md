# Design notebook for week ending November 25, 2015

## Description

My main accomplishment these past few days was figuring out how to change the `Decision` class
to account for the fact that either branch could end with a terminal node
that shouldn't converge with the other branch.
The main problem is that originally the `nextNode` for `Decision` refers to the node
on which both branches converge, but this makes the erroneous assumption
that both branches converge. To account for this error when creating the visual flowchart,
under this structure at least, `Decision` needs to know whether either branch contains a terminal node,
which is information that I don't think is appropriate for `Decision` to either know or compute.
Instead, thanks to my friend Savannah, I'm thinking I'll redefine `Decision`
to just have references to the first node in each branch.
It's then up to the parser to make the branches converge if necessary,
which is a fairly simple task. The thing I like least about this decision
is that `nextNode` needs to be removed from the the abstract class `FlowchartNode`
because it doesn't have an obvious meaning for a `Decision`
which goes to two nodes (the beginning of each branch).
This removal could result in an increase in type checking due to a decrease in conformity.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I need to change the flowchart abstract syntax to reflect the above changes.

**What questions do you have for your critique partners? How can they best help
you?**

Is this decision reasonable? Can you think of a better solution?
I also didn't finish the evaluation in time for my critique last time,
so if you could review that and lend me your thoughts that'd be cool.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Probably 4 hours: 1 hour talking with Savannah about the pros and cons of changing the abstract syntax
(we also discussed loops), 1 hour thinking about it on my own,
1 hour thinking about making the flowchart creation part more extensible, 1 hour on notebook.

## Post-critique summary

## Post-critique reflection
