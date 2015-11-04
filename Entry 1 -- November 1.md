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
He raised a concern about whether the language would induce an increase in comments,
and whether these comments would improve code readability.
He suggests that "all control-flow sturctures _should_ be documented,"
and in a similar vein believes users should receive an error
if only one branch of an `if`-`else` block is documented.
He proposes [Graphviz] for the flowchart creation language
because there are libraries for using its features.
He's curious as to my strategy for handling instances
when I get stuck or off track. And finally, he asks "Why Java?"

## Post-critique reflection

[ANTLR]: http://www.antlr.org/index.html
[ANTLR Grammars]: https://github.com/antlr/grammars-v4
[Codeviz]: https://github.com/JustisAllen/Codeviz
[Graphviz]: http://www.graphviz.org/
[JavaParser]: http://javaparser.github.io/javaparser/
