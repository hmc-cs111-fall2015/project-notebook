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

I forgot to poke them, but the critique has now been done!

I think that Robin did this critique (there is no name). Assuming that, he
said...

   1. The explicit type checks on input seem like a good idea
   1. I should put my logo in the repo.
   1. That two things come to mind with regards to suggestions

### Suggestions

On one hand I could have tab text-completion, similar to in an IDE where you
can type `circ`, hit `<TAB>`, and have then get `circle`.

I could also have textual suggestions displayed to the user, on start-up.

Finally, I could have the tab completion be rendered on the screen in gray (or
something like that).

## Post-critique reflection

I agree that text-completion would be neat, and complementing it with a visual
would be even neater. I think it would also be nice to interact with the
completion system in a more powerful way than just completing the names of
identifiers (and doing visuals).

In particular I think it would be nice to find out which inputs you can give to
functions. This is a slightly different type of query.

Perhaps it would be good to support both?
