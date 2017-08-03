# Design notebook for week ending November 23, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

I finally managed to make the parser be able to handle multi-word ingredients! I'm still forcing verbs to contain one word, as well as quantity types, though I may change this later if user feedback allows it. To do so, I had to compromise on making the language look like normal english and replacing `of` with `@` (because the regex parser needed the keyword between quantity and ingredient) to be non-alphabetical. I've spent a lot of time thinking about the data model and how to allow users to define and reference drinks within their script. It seems like the structure is going to have to look like this:

```
BEGIN LATTE:
stuff
END LATTE

BEGIN MOCHA:
LATTE;
add 2 spoons @ chocolate powder; 
END MOCHA

{
2 MOCHA 
1 LATTE
}
```

I think figuring out how to insert a latte into a mocha, though important, may need to be a secondary focus at the moment - the first task will need to be getting the parser to be able to handle this program syntax, and creating a data model for a recipe in the IR (maybe a recipe is just a list of instructions, but we need to allow multiple recipes in the AST, plus an imperative section that specifies how many of which drinks to make). What would be really cool is if I allowed people to have imports, so you could `IMPORT LATTE` and `IMPORT MOCHA` instead of having to define them in your script, but I don't know how to allow imports - maybe this can be a stretch goal.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The biggest implementation struggle this week is going to be adding in modifications and defining multiple drinks. I've found that parsers can be really hard to work with and I imagine making the frontend run will be the hardest part of this. Also creating a global namespace may be tough, but hopefully the material from the language features classes will be useful in this.

**What questions do you have for your critique partners? How can they best help
you?**

By the time you read this, I should have an implementation for the problems I detailed above. What do you think of it? Are there features that you'd like to see added to it, or to the language in general?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Probably about 5 hours so far, but I'm going to devote the entire evening (I'm writing this on Sunday afternoon) to it so it'll be at more than 9 by the time midnight rolls around. 

## Post-critique summary and reflection

Kevin proposed using a decorator design program for the language, where each type of ingredient has its own class and drinks store these ingredients and their quantities. I think the difficulty with this is that I want the users to be able to use whatever ingredients they want, and even if I create a case class for espresso and milk and other common ingredients, the user should be allowed to specify whatever ingredient they want (and maybe the invalid ones will be detected in the error checking stage). So I feel like giving each ingredient its own class can't mesh with allowing any ingredient the user wants. Another thing that Kevin said that really resonated with me was "I think what you ultimately need is a data model that represents different drinks, and a way in the langauge to define new drinks." This week, building the data model to represent a drink will be one of my main focuses. 

I agree that getting in my 9 hours is important - I've been able to get my time in this week, and plan to spend a lot of next week working on DSLs. 

As far as my implementation goes, here are the answers to some of Kevin's questions:
  - Drinks aren't actually defined as their own objects yet, but I plan to add in this functionality this week. 
  - So far, a user `defines` a new ingredient just by naming it, and all ingredients are treated the same by the language. Maybe this isn't the way it should be - I'll put more thought into it. 
  - What do you mean by "mixtures of ingredients?" Once I add in the ability to call drink macros, you could imagine creating macros for part of a drink as opposed to a whole drink. 
  - I do plan to build a data model into the IR; this is also something I'll work on this week.

