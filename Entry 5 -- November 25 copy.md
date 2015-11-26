# Design notebook for week ending November 25, 2014

## Description

I haven't taken much of a crack at my project in the past two days. Here I
depict the small amount of work that I did do and share my thoughts for the
future.

### Explicit Typing

Imagine a language in which all things are duck-typed. That is, the programmer
doesn't interact with their types explicitly, instead errors just get thrown
when invalid operations are done on those types.

Imagine Python.

In all seriousness though, as I move towards the program search & suggestion
part of the project I need to find ways to narrow the search space. One great
way to do that would be to filter by input types.

To that end I modified the AST, parser, and interpreter to support and enforce
the specification of the types of input parameters.

### Logo

We have a [first draft] logo now!

### The Future

The next stages for my project involve building the suggestion engine. I think
first I'll set up the interpreter so that it can undo steps, and then use that
to do possible constructions, report the results, and revert them.

I think it's neat that undo and suggestions seem like linked ideas.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I think my most pressing issues haven't changed much, although I'm glad to had
identified as a good first step towards suggestions.

**What questions do you have for your critique partners? How can they best help
you?**

I'm still very interested in hearing ideas about how the user might interact
with the suggestion system.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I've spent perhaps 2 hours outside of class so far.

## Post-critique summary

At the time of writing this my partner hasn't completed my critique yet. I'll
poke them tomorrow morning.

## Post-critique reflection
