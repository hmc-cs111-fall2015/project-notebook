# Design notebook for week ending December 6, 2014

## Description

11/30/15
1:15-2:30

Fixed parsing!
The tile's sourcepath wasn't properly parsing
Fixed: parse "FOLDER"+"/" repeatedly, then parse "tilename" + file extension, where file extension is one of many options.
Currently: have ".jpg"
Will have to add more (unforunately; there may be a workaround, but for now, leave it be)

Placing tiles works!
Debug maps for placing tiles works!

To do: Fix fill commands
Better error handling!

Now, fill commands work, but in strange ways.
Debug fill maps work perfectly.
When filling in rectangles, tiles are only placed in areas that they can fit 100% inside of.
When filling in other areas, they have strange behavior.
I need to get to the bottom of this, have better error handling, and then it will be complete.

Also, now the code can be run in Eclipse by entering the name of the map file, without the `.txt`, so long as the file is in the src directory. This may be changed later on.

The fill commands work properly.

Everything is implemented except for edges, which isn't too much of a deal.
Working on error handling. One question is, should users be allowed to draw things outside of the map?
For placing tiles and making areas, it may be useful. However, users would then be allowed to do things that are inefficient.
Ideally, throw a warning.

Some more error handling with the parsing, and then start making more tiles to continue with testing.

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
