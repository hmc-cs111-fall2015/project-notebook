# Design notebook for week ending November 30, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

All of my work time this week was spent making modifications work. First I changed the parser to handle the `({optional header}) body` syntax of the program. Then, I built up the Transformer object to take a program and turn the body into a list of RegularInstructions to execute. Now I'm debugging the Transformer object - while my code compiles and runs, the PrintBackend isn't printing anything out.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I've written the code for the Transformer, but it's currently buggy. Fixing that is the top priority on my list right now; everything else comes after.

**What questions do you have for your critique partners? How can they best help
you?**

  1. In my opinion, when I have instructions and modifications working, the core features of the language will be done. Take a look at testscript.caf and see if you disagree. In particular, are there other features that the language need before you'd consider it complete?
  2. Have a look at Main.scala. Do you agree with the design decisions I made around structuring the implementation (in particular, making the Transformer a separate step from the execution)?
  3. What would you suggest spending time on in the last week or so of class? Error handling? More features? A more robust backend?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I wasn't really counting, but I definitely spent at least 9 hours on the project this week; allowing for modifications and making them behave properly was a very heavy duty task.

## Post-critique summary

I never got a critique this week. 

## Post-critique reflection

See above.
