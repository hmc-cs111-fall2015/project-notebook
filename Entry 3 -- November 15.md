# Design notebook for week ending November 16, 2014

## Description

This week I added initial support for parsing processes/actions with the `//$` notation.
The method of doing so is a bit naive because it grabs all of the comments from the source file
in order but without regard to their position relative to grouping constructs
(e.g., loops and `if` and `try` blocks).
Ideally I think only top level processes should be parsed,
so I'll probably start there next week.

After I got the parsing functioning, I started looking into flowchart creation languages.
People had suggested [Graphviz]&mdash;which I had seen when first developing the language concept.
I wanted to do a bit of looking around for other flowchart creation languages before choosing Grphviz,
but I didn't find any viable alternatives. In looking into how I might use Graphviz,
I discovered that there is only an official library for C.
Thankfully there are also some user created Java libraries for using Graphviz.
I wanted the chosen library to be available on [Maven],
so I settled on the [Graphviz Java API],
which seems to work by writing in [DOT]&mdash;the particular Graphviz language
used for creating flowcharts&mdash;and then compiling the syntax to the appropriate figure.

Once I actually have to deal with parsing `if` statements,
I'll probably move to making some sort of `parse()` function.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The next big thing will be figuring out how to use the [JavaParser] output
in a way where I don't just retrieve all the comments at once,
and instead see the comments in relation to other constructs.

**What questions do you have for your critique partners? How can they best help
you?**

If you know of a better way to programmatically generate flowcharts in Java that uses a Maven library,
I'm all ears. The one I found isn't the most convenient,
but I think it'll do the job. Also if you look at my code
and think there's a better way to implement what I currently have, I'm all ears.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I probably spent around 7 hours on the project this week:
5 hours implementing initial process parsing
and 2 hours researching flowchart creation languages.

## Post-critique summary

Adam assuaged my fear that I might have to use the visitor pattern,
questioned the structure of the flowchart AST,
and expressed concerns regarding the opt-in philosophy.

## Post-critique reflection

### Language Choice

Adam reminded me that a benefit of using functional languages like Haskell
is that it's easy to add new functions to many classes; but in my case,
the number of functions I want to implement isn't increasing;
instead I want to add more classes that support a set of functions,
which is easier to do in an OOP language like Java.

### Flowchart AST

Adam had questioned the purpose of `nextNode` in the `Node` class;
I talked to him in person about this concern, demonstrating the intended purpose,
and he agreed that the proposed usage was appropriate.

He also suggested making `Decision` more flexible to account for switch statements,
but my current concern is to make `Decision` fit for `if`-`else` statements.
If I have time (which I doubt) after implementing other control structures like loops,
of which I have a better understanding of their flowchart representation,
then I'll begin to think about how to represent switch statements&mdash;perhaps
it's more appropriate to inroduce a new concrete `Node` class
than to make use of an existing one.

The AST is intentionally brief for the time being.
I wanted to start with some building blocks for expressing a flowchart,
use these blocks for code parsing and flowchart construction,
then expand or modify the block pool with successful integration
of each control flow construct. As for my initial thoughts on proper linking with subroutines,
I'm thinking it might be appropriate to add a `Node` that extends `Process`
with an additional field that points to the other flowchart.

### Opt-In Nature

I think users forgetting comments is a valid concern,
but I'd hope that they would examine the generate flowcharted
to ensure that it has the expected components; then if anything is missing,
they would reeamine their code to ensure they used proper syntax.
Ideally Codeviz will be clever enough to catch some user mistakes,
but I think it's reasonable to expect the user to carry some burden
of checking the generated flowchart to confirm it matches expectations.

To address some of the specific concerns raised:
If a section is uncommented, then nothing appears for this section in the flowchart.
This decision seems very reasonable to me. As I've mentioned,
I don't think users will want _every_ implementation detail to be represented in the flowchart,
therefore it should not be required that every "section" of code be commented;
a reasonable usage of Codeviz would be to highlight the high level control flow of a system,
which could easily mean using few comments in comparison to the amount of written code.
As for the case where an `if` statement contains Codeviz comments,
but the statement is not preceded by the appropriate Codeviz comment,
I think it's appropriate for the user to be given an error,
notifying them that a Codeviz comment marking the `if` statement was expected.

[DOT]: http://www.graphviz.org/content/dot-language
[Graphviz]: http://www.graphviz.org/
[Graphviz Java API]: https://github.com/jabbalaci/graphviz-java-api
[JavaParser]: https://github.com/javaparser/javaparser
[Maven]: https://maven.apache.org/index.html
