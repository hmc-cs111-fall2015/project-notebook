# Design notebook for week ending November 23, 2014

## Description

This was an extremely up and down week. It started off with making leaps and bounds on the front end and IR of my project getting to a point where, for the functionality I currently support, it is almost done. There are a couple more things to do but now we have a set up where the syntax looks like this:
```
Header:
	GroupSize: 3
	Names: Robin,Jackie,John,Marcus,Evan
	Interests: Math,Chemistry,Biology,Politics,Media_Studies,English,History
	Positions: Leader,Communications,Head_of_Design

Body:
	Groupee Robin:
		DontWantToWorkWith: Robin,Marcus
		WantToWorkWith: Jackie,John
	Groupee Evan:
		Interests:Math,Biology,Media_Studies
		Positions:Leader,Head_of_Design
		WantToWorkWith: Jackie,John
		DontWantToWorkWith: Marcus,Evan
	Groupee Jackie:
		Interests:English,History,Biology
		Positions:Communications,Head_of_Design
		WantToWorkWith: Marcus,Robin,Evan
		DontWantToWorkWith: John
	Groupee Marcus:
		Interests:Chemistry,Politics,Math
		DontWantToWorkWith:Jackie
	Groupee John:
		Positions:Leader
```
The program even does an intermediate verification that this is, in fact, a valid entry and hands it off to the backend to be processed. This is where the downs come in. After wrestling with/learning a variety of constraint solvers I've come to the conclusion that none of them will directly support what I  need. At this point Ive decided that I essentially have two options. I can either:
  1. disassemble the data and code it into integers and then decode it when I get the solutions (advantage of this is that it will have really good functionality and I found a great constraint solver that has built in weights) 
  2. write my own logical backend. This could be relatively quick and dirty and afford me more time to work on the language design aspects of the language but _this would be a sacrifice_ and would sort cheapen my final product I think. (i might be wrong about that)

Neither one of these options is great but neither one of them is horrible either. 
## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I need to figure out how I am going to handle the backend. This is a roadblock that I need to cross if I want to proceed.

**What questions do you have for your critique partners? How can they best help
you?**

I would love help on which of the above discussed options seems better, or if you think that theres a third (or more) option that I could consider.

Additionally, I'd love input on my syntax design. Do you think its intuitive? do you think its clean? what could be improved? etc.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

8-10 hours

## Post-critique summary

Anna suggested that I work on making my variables less clunky and add support for the existence of whitespace. She also agreed (with both Alex and me) that mapping to and from ints is the best way to proceed with the constraint solver.

Alex suggested I look into the possibility of changing what the parser considers "whitespace" or alter my pre-parser if I need to make more whitespace changes. He also suggested the addition of a newline/comma equivalence.

## Post-critique reflection
Anna's suggestion about making variables less clunky is great and is something that I've considered before. I think I realized how I can do it cleanly. The pyparser im using does not allow for the editing of what "whitespace" is but I think I can alter my prepass with no problem. The one thing is that I'm currently using new lines as significant characters for something other than commas, so I'm not sure if I can have it mean both. But I'm definitely going to look into it because _i really like that idea_.
