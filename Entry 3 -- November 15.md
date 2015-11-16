# Design notebook for week ending November 15, 2015

## Description

* Redesigned the overall structure of the code
* Came up with some new language features that would be useful
  * Simply querying a room name should show information about that room
* Redesigned the way that the parser works by seperating out statements, which start queries, and filters, which reduce queries to smaller results. Also have Joints which combine statements with filters, but might remove this as it is unnecessary since single queries 
* Backend design
  * The preliminary backend should just be able to put together a text response for the given query
  * OR for requests, it will return a text response for succeeding or failing (and why it failed)
* Most of the errors from last week are now fixed -- however this took so much time that the overall parser is incomplete.
  * I'm taking advantage of the garden parser as an example, so the project repo currently holds a copy of that file.
  * The AST is now complete
  * For the prototypes, I will be presenting a paper prototype

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I need to sit down and finish the parser. 

**What questions do you have for your critique partners? How can they best help
you?**

Please look over the AST and how things are starting to shape up in the ir and suggest changes!
I have no idea what to add in for syntactic sugar, so any suggetsions here would be great.
Do you have any suggestions for interfacing with a query based system?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I spent about 8 hours on the project this week, including studio time. 
I didn't quite hit 9 hours due to some other obligations this week.

## Post-critique summary

Zoab made quite a few helpful suggestions. 
His suggestions cover project scope (and by extension functionality/extensibility) and gives lots of good ideas of ways of expanding the project.
They were focused to HMC's facilities, and for the scope of this project I think that is appropriate.

## Post-critique reflection
While I do agree that to have a powerful and useful EMS system, the functionality will have to be expanded on quite a bit. However, I don't think I can manage building out a complete system while focusing on the langauge aspects of the project. So, a lot of his suggestions I will leave for the last week and get to them as time permits.
The current scope of the project is to focus on building out a prototype of the intermediate representation and then focusing largely on the parser/language aspects. I think there will also be langauge features I will not get to because their ir is difficult to implement but those will be documented in the future.
