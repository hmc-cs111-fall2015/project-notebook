# Design notebook for week ending November 30, 2014

## Description

I spent some time finishing up logging and verbose options.  At this point it should
be moderately easy to use (I'll address Adam's concerns from his critique below) and
should be somewhat thorough, however I don't yet have tests for that... I should
write those.

I also implemented my first mechanism! At this point in time you can run simple acid
base reactions, if you tell the system exactly what about them is acidic or basic and
let the program know what parts should react together.  It also won't work with multi
component reactions - only a single acid with a single base.  It also doesn't handle
disassociation, so it can't do HCl + NaOH -> H2O + NaCl, but it can do H + OH -> H20.

I've also started work an actually computing the acidity/alkalinity of the molecule,
however this doesn't work yet, and has actually revealed a strange bug I believe is due
to a circular import somewhere.  Once I've fixed that (it will probably require some
reorganization of the modules) I should be able to make decent progress on predicting
the pKa of a molecule.  

Lastly, I've started work on loading molecules from file.  Unfortunately, getting
[openbabel][1] to work and build for me has been quite non-trivial, and for now that
has been stalled.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

If the way I've implemented mechanisms and requirements seem reasonable, and if it
seems like too much work for the user.

**What questions do you have for your critique partners? How can they best help
you?**
See above.  I've also addressed many of the concerns of critique partners from the
last few cycles (in the develop branch, has not been merged to master at the time of
writing) and I'd like to see if those address those concerns well.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Between Sunday, 11/22/15 and Wednesday, 11/25/15, probably 6 hours? And I'll probably get
a few more in over break, so hopefully a total of 10-12 by next Sunday.

## Post-critique summary

The current syntax of injecting logging into functions is unpleasant. Additionally, 
logging within a mechanism or requirement may not be as useful.  The current syntax
is a little cumbersome.  I should realize my focus as writing extensions of the language,
not as `react()` which is too narrow a focus.  Requirements should return a floating point
number that represents how likely they are to occur based on that requirement.

## Post-critique reflection

I agree. I didn't initially see a good way to do this, however [this answer][2] seems to 
indicate it can be done in a moderately hacky way.  I like the point about logging levels,
and I wonder if maybe I should require that the requirement functions also be decorated so
as to inject the logging into them as well. I've added a number of the suggestions regarding
syntax and want some feedback about my implementation choices.  I agree about the focus question.
Lastly, I like the plan for floating points, and it aligns with my current plans - I can give a
value of 0 for a no-op, a value greater than 0 and less than 1 for forward reaction (closer to
one is a more strongly favored reaction) and negative values up to -1 to represent a reverse
reaction.


  [1]: http://openbabel.org/wiki/Main_Page
  [2]: http://stackoverflow.com/a/17862336/3076272
  
