# Design notebook for week ending November 16, 2014

## Description

Yikes! What a week. I started the week considering a couple of options (scala external, prolog internal) and now here I am on sunday and I'm doing neither. I tried to get into the Scala but it was just too tough for me to try and get into a new language and a concept that I was having a hard time understanding (parsing). In response to that (after spending 3-4 hours wrestling with Scala) I bailed out and am going to do a _python external DSL_.

After getting aquainted with the Python framework for parsing ([PyPeg2](http://fdik.org/pyPEG/)) I dove in and wrote the complete parser. At this point it's not perfect because I couldn't figure out how to make the parser read new lines (I think that right now the parser removes _all_ whitespace. I'm trying to figure out how to toggle that off) so I've replaced newline characters with a couple of random characters (`'+','-'`) to serve as placeholders until I get the whitespace working. 

There are a couple of python constraint solvers that I'm considering and I'm actually pretty excited about them. The first one (and the one I think I will use) is [Python-Constraint](https://labix.org/python-constraint). This has really clean syntax and nice support for features and might even support soft constraints! The other is [Numberjack](http://numberjack.ucc.ie) another solver, but this one does the underlying computation in C/C++. I think that `Python-Constraint` is probably a _cleaner_ tool but I think that `Numberjack` is probably more flexible/powerful. __I'd love your feedback on which of these tools to use!__

## Questions

Next on the docket for me is going to be writing testing and checking for my parser (is it in the correct format? is the data in the body relevant to the data given in the header? etc). I also am going to start implementing the constraint solver with the data received from the parser. I need feedback on which constraint solver to use and also any design feedback you have on my intial syntax. 

**What questions do you have for your critique partners? How can they best help
you?**

Which constraint solver looks best to you? What do you think of my language design? What do you think should be my next steps?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I probably spent 6-8 hours outside of class. It was a frustrating week because I spent a lot of time wrestling with/writing scala and then ditched all of it but I am feeling a lot a lot better now that I'm writing in python. Previously the project was feeling ominous/scary and now I'm really excited about working on it.

## Post-critique summary

## Post-critique reflection
