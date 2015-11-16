# Design notebook for week ending November 16, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

I've checked some items off my to-do list. I switched the keywords in the parser for generic JavaTokenParser idents, which allows someone to truly specify whatever verb, quantity typename and ingredient name they want. I still need to add error-checking into the language, though. I also modularized the print backend a bit more. I'm considering making a second backend as a next step to get an idea for how my generic backend API needs to look to handle multiple backends. 


## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The next language design step for me is going to be figuring out what to do about modifications. My next actionable item is probably going to be writing a better readme for project demos tomorrow, so that people know how to use the language. My next implementation-heavy to-do will be adding the ability to extract quantities from whatever units the user inputs them in. I suspect this may involve using the squants library as well as playing around with extractors. 

**What questions do you have for your critique partners? How can they best help
you?**

The next big thing on my list is creating the ability to modify existing drinks. According to Prof Ben, there are 3 major ways to extend existing recipes:

1. Add stuff (LATTE + whipped cream).
2. Take away stuff (LATTE without coffee).
3. Modify stuff (LATTE with skim milk).

The main question I have for my critique partner is as follows: 
How would you recommend implementing modifications (of all three types)? 

Here are some ideas/more specific questions I had:
It seems like modifications could operate on the AST of "regular" instructions and change the recipe into its final ready-to-execute state. How would I store modifications? Would they just be a different kind of instruction, or maybe the parser would put them into a different object, that has a method to accept a set of instructions and run the modifications on it? 
What's an elegant syntax to put on the language that allows modifications and drink macros in a reasonable way? The idea I had so far was to make a language keyword like `modify` which would indicate that an instruction was modifying the current drink instead of adding a new instruction, but I'm not really sure what to do with this.  
Is having imports worth it (ie, importing recipes from other files vs having to include all recipes in the same file)? How do you even make imports work in a language? 


**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

This week was a rough week; I had a lot of work in other classes that took away from my DSLs time. Including class time, I probably spent about 5 hours so far on my DSL. 

## Post-critique summary

Alex thinks that I need to work on the system for specifying quantities a bit more. In particular, he thinks that I should implement weighting the quantities of ingredients and having the system calculate the exact quantities of material required. 

As far as the future of the language goes, he encourages me to think more deeply about calling drinks inside of other drinks and how this will affect the end product (the ratios of ingredients, etc). 

He argues that I need to start making some decisions about what I'm going to allow my users to do in this language, because we don't have that much time in the last few weeks of the semester and I should know what I'm aiming for to make writing actual DSL code easier. 

He also thinks that verbs may not be necessary for the language (what's the difference between scooping and sprinkling some material?) and that I need to write a README for the language. 

## Post-critique reflection

I absolutely agree about the README thing; in fact, this is something I should have done before class tomorrow so that people are capable of using my prototype during the demos. Working on the system for specifying quantities is also another important thing to tackle soon - I'd been avoiding it because I couldn't come up with a perfect solution that would be easy to implement and capture all use cases, but I think I'm just going to have to hammer out a prototype and see how well it works. Calling drinks within other drinks is also going to be a pain to figure out - I think I'll start by writing out a concrete example of the code that a user should type and the function that code should perform, and then based on that I'll generalize the concept of calling drinks within other drinks.

I disagree that I need to start making decisions about what I'm ultimately going to allow users to do in the language - now that I have a working prototype (that compiles and runs!) I can just iterate over it repeatedly adding new features until the end of the semester. I don't think it's the case that I need to have a final vision for the language because the final version will just be what I have now with as many features and changes as I can stuff into the next 4 weeks. 

I kind of agree that the verbs may not be different in meaning for the print backend, but they may be useful for another of the backends - the verb used when adding an ingredient does matter in recipes in general, after all. I spoke to Prof Ben and he saod that even if none of the features I write involve using the verb, if someone else extends the language they may need access to the verb and including it in the IR allows them this access. Plus, if I'm going to require them to use some verb in an instruction anyway (which I will, because `2 shots espresso` is not a coherent instruction), I might as well hang on to it in the IR in case it's useful for something. 