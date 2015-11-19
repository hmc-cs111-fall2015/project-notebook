# Design notebook for week ending November 23, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

In class prototyping, we discussed a few things 
- Allow for intervals, monthly daily or weekly
- Monthly Recur model, allow for it
- define date ranges that can be used in other scopes


Now that my prototype is done and working, I have to start thinking about additional
features that would entice a person to actually use this product, and to makes sure
it works they way they want it to. One of the biggest things people use differently
is date formatting. I haven't thought of a perfect solution yet for this. 


As I have been looking over and reviewing my code, here are some things I think
are vital to add if this is actually going to be used by people:
- Some way to use different date/time formats. This could be automatic detection
or having default settings that could be changed in a settings header. 
- redesign syntax so that curly braces are not necessary. Since my parser already
has things being interpreted without looking for a closing curly brace, I think this
is a trivial addition. Would require some user testing though. The only problem here 
is with sections. Since they kind of need it, will it be confusing if they are the 
only one using it?

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
