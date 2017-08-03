# Design notebook for week ending November 30, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

This week has mostly been dedicated to finishing the modifications feature. Right now, I've implemented the syntax and semantics of the four different types of instructions (regular, remove, swap, and make) and these work as expected. I haven't done anything special to handle mutual recursion (Scala barfs with a StackOverflowException) or check that a make instruction references an existing recipe - I just find any recipe whose name matches that of the make instruction and add it to the result. This also causes strange behaviour if a recipe is defined twice - which it really shouldn't be. 

I'm pretty happy with where the project is right now, which is good. Handling modifications is the biggest feature that the language needs to have, and I have a working (if rudimentary) implementation of that right now. I think I'll probably spend the next week on trying to resolve some of the issues I mentioned above (putting the recipes in a HashMap instead of a list might allow me to clean up the code a bit, for instance), as well as working on the final writeup. Overall, I think I'm in pretty good shape! 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

At this point, I need to start putting some polish on the project (going through and adding comments as necessary, for instance) as well as getting the final writeup together. I probably have time to add one more small to medium sized feature to the language -- I'm leaning towards adding error checking for basic semantic errors - referencing recipes that don't exist, defining recipes twice, that kind of thing. It would be really nice to be able to warn someone of mutually recursive recipes, but that would involve creating and evaluating a dependency graph which might be too big a feature to add so late in the semester (I know it's time consuming because I tried to implement one for a Databases lab, and it proved to be too difficult so I abandoned it). My other classes have also been picking up as we near the end of the semester, so I imagine 

**What questions do you have for your critique partners? How can they best help
you?**

What kinds of semantic errors should I be aware of as I add error checking to the language? In what ways could a program in this language be syntactically valid but semantically incorrect?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I've probably spent about 6 hours on the project this week. I would have gotten more in on the weekend, but I fell sick on Thursday, which put me out of commission until Sunday morning or so. 

## Post-critique summary and reflection

When reading my latest testscript.caf, Alex found the program to be very hard to understand. He thinks the syntax of the language is misleading - for instance, having a make instruction in the body of the program and then some modifications below it don't make it clear that the modifications are affecting everything above them in the instruction buffer. I think his suggestion of having the syntax look like 
```
start LATTE;
<modifications>
finish;
```
might look cleaner, but this assumes that the language has some notion of scoping, which it doesn't really. Adding in scoping might be too ambitious for the last week of the project, but I can certainly look into ways to make the syntax clearer. I'm not sure how to make the syntax unambiguously clear, though - would changing the syntax so the language is more understandable for some users make it less readable for others? I guess I could try to run my syntax by multiple classmates and make changes only where the majority of them feel that the changes are appropriate. 
