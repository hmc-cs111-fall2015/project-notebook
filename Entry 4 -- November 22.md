# Design notebook for week ending November 23, 2014

## Description

This week I finished up my molecule data structure (at least the initial parts).
A big change was that I ripped out registering the molecule type - I realized 
that if a user wants to use their own custom data type, they just need to do that
within their mechanism function.  As long as it returns something that I can work
with, it should be fine.  

I also started on adding logging and verbosity options, which at the time of writing
are not complete, but I hope to add them before class on Monday.  Essentially I want
to provide thorough logging of events (currently I provide very little information
beyond logging error cases).  Ideally, by decorating a reaction mechanism, it should
add a `logger` attribute to the function object. This would allow end-users who extend
the language to have their own mechanism log to the same place that the rest of the
application does.  For example, if I change `ReactionDispatcher.__call__` to look like
this:

```python
def __call__(self, function):

    function.logger = self.logger
    
    return function
```

then people who register their function can do this safely:

```python
@register_reaction_mechanism(...)
def my_mechanism(reactants, conditions):
    my_mechanism.logger.log("Performing a my_mechanism type reaction")
    ...
```

or something similar.  

I've also started planning out my generic acid-base reaction.  I've worked out the
encoding I'm going to need, as well as the requirements (I think), however I haven't
written any code yet. While the details of that are somewhat chemistry heavy, and
actually implementing some of it will be quite hard (for example, calculating the
pKa of a molecule, which is vital for predicting an acid-base reaction, is actually
quite tricky), I hope to at least have a mock-up ready by presentation time (I might
just get the pKa from the conditions, and require the user to enter them, for now).
This is what I plan to spend most of next week on and I'll talk more about it then.

I also haven't really implemented any of the suggestions from class last week, mostly
because I've been quite busy, however I hope to implement some of them this coming
week as well.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Right now I'd appreciate thoughts about what sort of diagnostic information is most
useful to an end-user, and if that information is helpful.  Additionally, continued
suggestions about registration, dispatch, and using requirements would be welcomed.

**What questions do you have for your critique partners? How can they best help
you?**

See above.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

10 hours.

## Post-critique summary

_Matt's critique_
I haven't abstracted away chemistry details because there are none yet. Dispatch on
dynamic predicates will be slow, and will probably not be easy to optimize, and was/is
easy to implement. I should probably think about if I want to continue focusing on the
dispatch side of things, or the chemistry side of things. An object type instead of a
dictionary might be useful.

_Justis' critique_
Well commented, thoroughly tested.  Names aren't quite as friendly as they could be - 
rather long.  I should consider talking to some chemistry profs about what I'm working
on.  In particular, before making it more general, see if it meets the needs of users.

## Post-critique reflection

I like a lot of the suggestions about syntax and implementation that Matt gave, and while
I haven't implemented any of them yet I plan on thinking more about them later.
Additionally, I plan to talk to some professors like Justis recommended, although not 
necessarily for this class but rather for future development.
