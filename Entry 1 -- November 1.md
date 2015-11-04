# Design notebook for week ending November 1, 2015

## Description

I spent this week researching tools for parsing Java and Python,
which are the two languages I'm considering for the underlying language
for (at least one of the first iteratons of) [Codeviz].
I spent more effort researching Java because I think Java stands to benefit
more from Codeviz than Python, since (as I think most people would agree)
Python is more readable. That said, the main reason I was considering Python
is that I was of the belief that there would be more support for parsing Python.
Through my research, I believe I found that the developers of both languages
provide an abstract syntax for parsing needs; however,
neither of these syntaxes include comments,
so I was forced to look beyond the language documentation.

In my continued research, I stumbled upon [ANTLR], which actually seems like
it could be _super_ helpful to someone in the class. I haven't looked too much into the tool,
but it appears to generate a parser based on a given grammar.
There's a [GitHub project][ANTLR Grammars] in which there are grammars
(and therefore parsers) written in ANTLR for a **lot** of programming languages.
I didn't end up choosing the corresponding ANTLR Java parser because I found [JavaParser],
which seemed more straightforward, better documented, and better supported.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The next thing I'd like to do is make sure JavaParser will work for me.

**What questions do you have for your critique partners? How can they best help
you?**

It would be cool if my critique partners could look over the description and plan
and add any questions, comments, concern; is anything unclear?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I probably spent about 2 hours researching parsers,
and another 5 hours on the description + plan writeup.

## Post-critique summary

Dan had a fair amount to say about various parts of the project!
He raises a concern about whether the language would induce an increase in comments,
and whether these comments would improve code readability.
He suggests that "all control-flow sturctures _should_ be documented,"
and in a similar vein believes users should receive an error
if only one branch of an `if`-`else` block is documented.
He proposes [Graphviz] for the flowchart creation language
because there are libraries for using its features.
He's curious as to my strategy for handling instances
when I get stuck or off track. And finally, he asks "Why Java?"

## Post-critique reflection

One topic Dan picked up on that I've honestly been concerned about for some time
is whether the comments users will be adding to generate the flowcharts
will obstruct code readability due to the number of comments added.
I think in the early stages of the language, these comments will indeed
obstruct code readability for this reason; but one feature
I think will alleviate this problem is enabling inlining of function comments
whenever a given function is called: a user includes a Codeviz comment
describing the function's behavior before the function's definition,
then whenever that function shows up in the code,
the description appears in the corresponding place in the flowchart,
allowing users to reduce the number of comments explicity written in the code.

To answer Dan's questions, I _hope_ that the language will ultimately lead
to an improvement in the readability of the code itself
since users must comment their code to benefit from the flowcharts,
but I'm aware the early stages of the language will have the opposite effect.
Regardless of whether there is an improvement in readability,
I think Codeviz will induce an increase in comments&mdash;though
I don't think this is necessarily a bad thing.

I mentioned that Dan suggests that "all control-flow sturctures _should_ be documented,"
but I'm not convinced. I think there may be times when we want the flowchart
to represent a high level algorithm, but the code implementing the algorithm
for some reason uses an `if` block in response to an implementation detail
that we don't want to leak into the flowchart. I suppose I'd agree that I'd expect
_most_ control flow structures to be documented, but I'm hesitant to agree that _all_ should;
further, it seems important that the underlying language's syntax not leak into the flowchart
so that the flowcharts are more accessible to non-programmers.

I'm only slightly hesitant to produce an error when only a single branch is documented
because I think there might be a valid usecase, but I'll probably just make it an error
until someone complains (at which point I'll reconsider) since in most cases,
users should probably be documenting all branches.

I'll note that Prof Ben also suggested Graphviz to me.
I'm still going to do some research into other flowchart creators,
but it seems I'll probably be using Graphviz for the project.
(Also Codeviz derives from Graphviz.) :relaxed:

If I get bogged down in details or get stuck, I think it'll help
to discuss the problem/current work with peers and Prof Ben.
It'll also help to continually evaluate whether the current thing on which I'm working
is actually a priority.

Java is both the language in which I intend to implement
the first iteration of Codeviz and the first language Codeviz will support&mdash;and yes,
one of my first thoughts was that I'm hoping to include Codeviz comments in the source code.
:stuck_out_tongue_winking_eye: My main reason for choosing Java
as the first supported language is that the language is currently very popular,
and I want to maximize my impact.

Lastly, I just wanted to note that it's been affirming to see
that people are interested in the project.

[ANTLR]: http://www.antlr.org/index.html
[ANTLR Grammars]: https://github.com/antlr/grammars-v4
[Codeviz]: https://github.com/JustisAllen/Codeviz
[Graphviz]: http://www.graphviz.org/
[JavaParser]: http://javaparser.github.io/javaparser/
