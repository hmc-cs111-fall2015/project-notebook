# Design notebook for week ending November 9, 2014

## Description

#### Wednesday November 4
Today I was thinking a lot about how I wanted to attack my project. My default plan is a parser and constraint solving library in Scala but I also think thats not very sexy. Prof Ben set me up to have a meeting with Prof Keller on Friday where Im gonna learn about the possiblity of an internal DSL in _prolog_.

When I was thinking about kinda whacky solutions to my problem, though I got the idea to try and do something in [Mathematica](https://www.wolfram.com/mathematica/). I spent a long time getting back into it and I think it is a possibility but there isnt really a great infrastructure for doing constraint/logic programming. I think that, while I want to make Mathematica work because I think its awesome, Mathematica is _probably_ not the answer here. :(

#### Thursday November 5
Thinking more about my possibilities I'm becoming more resigned to the necessecity of an external DSL in Scala which, while I might not think is as _cool_ as some other options I'm considering, is probably a good solution. I'm still waiting to see what is said about internal DSLs in prolog but its seeming unlikely that I go that route.

Today its also been good for me to try and do some constraint programming in Prolog just to see what it feels like, try and make sure I can get the solutions I think I should get based on constraints I set myself. Basically I want to be able to make sure that I can use constraint solvers to do the same logic my brain does, (on a scale that is small enought hat my brain can contain the whole problem) so I can trust it to do larger computations once my brain can't contain the whole problem (the whole reason I'm doing this project ;))

#### From Friday Nov 6
Was planning to meet with Prof Keller to discuss internal DSLs in prolog but the meeting didnt work out cause I had forgotten about another meeting I had scheduled. I'm going to have to just get started on the Scala project and then (if prolog really calls my name) go back if necessary.

### Sunday Nov 8th
Spent a bunch of time considering the syntax of my language, trying to figure out what is going to be the most intuitive and easily used way of describing problems in my DSL. One thing I have been thinking about is whether I should ask for a list of possible defining characteristics at the top of the file (so I could have a little more ability to check at compile time) or just pick up a list of them based on all of the inputs. See the mockup.txt file in the Grouper repo for more info about what I mean. 

## Questions

Right now my most pressing issue is to start getting code down on paper I think. I have spent a bunch of time in limbo because of how sick I was and then trying to wait and see about the best option for implementation of my language. Its important now for me to just go for it and have some fun.

I would like feedback on my syntax design choices, and then as I start writing the parser I'll want feedback on that as well.

## Post-critique summary

## Post-critique reflection
