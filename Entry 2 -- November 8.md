# Design notebook for week ending November 8, 2015

## Description

* I decided to write the API in Scala. I don't think the language choice is as important as the design choices I will be making for the language component. I choce scala because it will make it easier later on to hook-up to the front-end since the front-end will be implemented in Scala.
* This submission is _hopefully_ a viable implementation of the API. For now the data model is very simple.
* I decided to create the underlying data model to have a manager (the class that API calls will go to), rooms (which holds schedules), schedules (which hold occupants in hourly slots for the seven days of the week).
* The project plan seems to be working - 
  * This week I worked on API with a basic local storage back-end 
  * Next week I will work on: 
    * Adjusting API with critiques
    * implementing basic front-end language ideas

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I feel like my API is rudimentary at best. I spent a lot of time this week writing and rewriting the API structure because I couldn't find something I was *too* happy with. Any suggestions in this department would be helpful. Also, ScalaIDE/Eclipse dislikes my program structure and is unable to recognize class names in the same package. I spent some time trying to fix this issue but I think I will have to go to office hours/grutoring to try and fix this one.

**What questions do you have for your critique partners? How can they best help
you?**

What do you think about the API?
What kind of API calls do you expect to be able to do through a space management system?
Do you notice anything blatantly unintuitive in the function calls?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I spend about 9 hours this week including class studio time.
About 2 hours spent (wasted?) on trying to fix my project within Eclipse. :-(

## Post-critique summary

## Post-critique reflection
