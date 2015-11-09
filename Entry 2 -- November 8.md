# Design notebook for week ending November 9, 2014

## Description

A lot of the description of what I've been looking into this week
is [ https://github.com/MatthewValentine/project/blob/master/documents/design_and_implementation.md | here ],
in design_and_implementation.md.

Specifically what I've done is a cursory examination of Template Haskell,
and then look more deeply into MetaML and Lightweight Modular Staging.
MetaML is pretty close to what I had been imagining for my project
in the first place, and LMS has some additional useful features beyond MetaML.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue at the moment is that I need to try out implementing
something using LMS. Alternatively, to implement a small version of LMS
itself if it seems straightforward to do so, but that is unlikely.

**What questions do you have for your critique partners? How can they best help
you?**

I'm not sure. Here's a question. Prof Ben mentioned that since metaprogramming
techniques like LMS are useful for creating DSLs, it might be an OK result
if my project turned out to be a tutorial of sorts on those paradigms,
if I was unable to actually make using them easier.
That seems like it would be a little odd in terms of the class,
and I don't intend to go that way, but what would your feeling be on that?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Around 14 hours.

## Post-critique summary

The most exciting possible feature of this project is the way
that it could offer even greater levels of extensibility to programmers.
Even so, the project is extremely broad.
Easily-implemented 

## Post-critique reflection

While doing my research, I came across MetaML. MetaML implements a lot of the
ideas that I had been having about what I wanted to do. However,
MetaML, LMS and other related things have a different focus than
what I was looking for. Typically, they are especially concerned with
code generation for the purposes of performance.

But adding language features and extensibility was the exciting idea
of my project. So, bending these other tools to produce that result
could be quite enough of a project, and worthwhile.

