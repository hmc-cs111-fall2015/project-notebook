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

The most important next step for me is figuring out which feature to build next. The factors that I anticipate going into this decision are as follows:

1. How hard will it be to build?
2. How badly do I want it to be part of the language?

I'd like to start off by building the "easier" features, and then move on to the more techinically challenging features as I get more used to the mechanics of programming in Scala (it still feels somewhat new to me, though I've been able to understand and diagnose errors somewhat better of late).

I plan to discuss this with Prof Ben on Monday, as well as (if possible) my critique group. 

**What questions do you have for your critique partners? How can they best help
you?**

What feature(s) would you suggest adding to the language next? What would you (as a user) most like to be able to say in this language that you can't in its current form?

I think I should put off adding any error checking at all until my language is more complicated, at which point I'll (presumably) have a larger number of errors to look for, but if you disagree with this decision let me know.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

All told, I probably spent 9 hours, or maybe a bit more, on the project this week. I think that's alright because I didn't spend enough time on the project last week. 

## Post-critique summary

Kevin's main critique of my project plan was the lack of good metrics for how well the project is going. In particular, he thinks I should flesh out my quantitative metrics a bit more. In addition, he approves of my implementation plan and leaving time to add polish. He recommends including evaluation time in the plan. 

As far as the project description goes, figuring out exactly who the users of the language are seems to be the most important thing to do. The question of whether the language is meant to be written by your average Joe (no pun intended) or recipe makers is an important one to answer. Kevin also suggests supporting defining quantities both by weight and by absolute measurement, and letting the system take care of the implementation details.

## Post-critique reflection

I agree that finding some way to cost the various features would be a nice thing to do (a la Pivotal Tracker), but I can't think of how to. I sort of have a feeling of which features might be easier to implement than others, but I don't really have a good sense for how many hours I'll be working to implement a particular feature. Maybe this will come in time, as I add to the language?

As far as qualitative metrics go, I'm pretty happy with a subjective evaluation of the feel of the language. In particular, I feel like I'm building this language more for myself than anyone else (at least for this class), so I would trust my gut feeling about how satisfied I am with the language as an indicator of success. I agree that user surveys are also important, since the language's end users are not just me, and I definitely want to catch bad user experiences so I can improve them. However, it seems like since I have a vision for what I want the language to be, I'm most fit to evaluate where I feel like the language is compared to my vision.

I agree that figuring out who exactly the users of the language are is an important goal. Ideally, I'd like the users to be able to be anyone (as opposed to a set of recipe makers), but this would require more features to be enabled (for instance, the ability to specify what ingredients we have available and the size of the cup), so we'll see what happens there. The need to have more features to support the average user than a recipe designer is why I've kind of held off on making that decision, since I figure if my language doesn't have enough features by the end of the semester I can just say "Oh, that's because it's for recipe makers, not ordinary people". Similarly, if I can allow users to specify weights or absolute measurements and take care of the conversion under the hood, I will, but I'm not sure how hard it'll be to create this feature (in particular, this may add some challenge to building the parser). 