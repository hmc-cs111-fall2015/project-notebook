# Design notebook for week ending November 9, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

**It works! It actually works!!!**
This week, I built out a very early stage prototype for the language. It compiles and runs and all. The code design looks very similar to Piconot-external (minus the error checking), and the only backend implemented is the one that prints out the steps being executed in order. Unsurprisingly, it's missing a lot of the features that I'd like the language to have - for instance, specifying ingredients by weight instead of absolute quantity, and the ability to create "functions" (really they behave more like macros). The language also doesn't have any error checking at all, which seems like an important language feature to add. My goal for the next few weeks will be to add features one at a time, as well as to create additional backends for the language to demonstrate its flexibility. That said, I'm really glad I have a working proof-of-concept now, and am excited to improve it inthe coming weeks. 

For reference, here's what a sample program looks like:

```
add 4 shots espresso;
pour 3 oz milk;
scoop 2 spoons sugar;
sprinkle 10 grams cinnamon;
```

And here's the output from running this program:

```
adding 4 shots of espresso
pouring 3 oz of milk
scooping 2 spoons of sugar
sprinkleing 10 grams of cinnamon
```

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most important next step for me is figuring out which feature to build next. 

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

All told, I probably spent 9 hours, or maybe a bit more, on the project this week. I think that's alright because I didn't spend enough time on the project last week. 

## Post-critique summary

## Post-critique reflection
