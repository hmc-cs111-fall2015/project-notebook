# Design notebook for week ending November 22, 2015

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

* I just realized that my understanding of how the AST and Parser should work together (and ultimately how the interpreter works) was fundamentally flawed... Not *too* bad, just have to rewrite the AST.
  * On the bright side, what I thought I had to do was much more complex then what actually needs to be done :-)
  * On the not-so-bright side, I think I would be done with the parser by now if my original understanding was the correct one.
  * The realization also moves a lot of the work in the ir into the back-end so I am not scrapping all of the work!
* From the studio prototyping, I worked out how to distinguish my language from an application. While building out the first API and otherwise, I was really afraid I was just building an application rather than a language. Working with Daniel Houck answered a lot of critical questions about how to keep the langauge exactly that _just_ a language.
* I restructured the AST to match more closely to what I want to do. I'm still having a lot of trouble making progress on the Parser. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Write the parser!!! Abandon all other commitments!!!

**What questions do you have for your critique partners? How can they best help
you?**
How would you go about designing the parser for this language? I pushed the new AST to git but only have some rudimentary Parser code.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

This week, I had a number of interviews and deadlines that crept up on me and unfortunately I wasn't able to spend that much time to sit down in front of a computer and implement more of the language. 
I did get time to continue to play around with different language ideas with pen and paper as well as write out some thoughts I have about _how_ I should design the parser.
Overall, I spent about 8 hours this week on the project incl. studio time.

## Post-critique summary

I didn't get a critique? Unless I missed it.

## Post-critique reflection

:-(
