# Design notebook for week ending November 30, 2014

## Description

This week was pretty implementation light.  I switched coverage systems (from 
coveralls to codecov) and added a static analysis tool (codacy), as well as
fixed some compatibility issues with Python 2.6 and 3.x.  I also tried to get
file loading working again, but I'm still running into build errors on travis.
I spent a little more time trying to calculate pKa, but didn't make much progress
(I don't believe I actually pushed any of those changes out).

The rest of my time was spent writing and practicing my [presentation][1].  Not
everything in that exists yet (or even will by the 11th) but it is a pretty good
representation of what I'd like to continue doing moving forward.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Expanding existing functionality, and cleaning up existing funcitonality.  Mostly
paving the way for future work.

**What questions do you have for your critique partners? How can they best help
you?**

Are there any glaring issues that stand out to you?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

8 hours or so.

## Post-critique summary

My logging idea might not be ideal - why stick it into globals automagically instead
of importing it.  Interacting with molecules is the trickiest part.  Creation could
be cleaner, but reading from file is probably the best system. Labeling could be clearer.
Arbitrary data could be stored in molecules instead of conditions.  A database could be a
nice addition.

## Post-critique reflection

I agree - sticking it into function globals is pretty silly.
I agree here as well - molecules are tricky buggers.  I like the idea for creating new ones -
I'll look into it.  I agree with the labeling points - it could use work, I just chose this
for the sake of simplicity implementation wise.
I didn't have any good reason for putting that arbitrary data in the conditions.  I just stuck
it there because it was convenient and temporary.
Using a database would be nice, but I think I'd try to tackle naming as per [IUPAC][2] standards
first as a better way to search the database.


  [1]: https://docs.google.com/presentation/d/1IUTd_rd_jTPNlQTdsM_yQXDmbSqj9AkcUFA3vtc_Oe4/edit?usp=sharing
  [2]: http://www.chem.uiuc.edu/GenChemReferences/nomenclature_rules.html
