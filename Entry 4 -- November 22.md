# Design notebook for week ending November 22, 2015

## Description

I started this week by updating the parsing logic to only grab the top-level comments
as opposed to _all_ the comments in the file.
"Top-level" currently refers to comments outside of Java constructs such as `try` and `if` blocks.
Additionally, only comments in the first method named "main" in the first class are parsed.
I'm hoping to replace this second constraint with a more flexible one by the end of the semester.
I'm targetting the `public static void main` method
(though I currently don't check the signature of the parsed "main" method),
but there should be a way to indicate what methods should have flowcharts generated for them.
Prof Ben mentioned using annotations to achieve this, and I'm very fond of that idea.

After achieving the more selective comment parsing, I refactored the code to use more helper functions.
In doing so, I started feeling uneasy about how much I was using `null` to represent a 'non-result;'
and then I remembered hearing that Java 8 has [Optional], so I refactored the code to use Optional,
which feels a bit clunkier than I would like, but I think it's better form.

In refactoring the code, I also added new Codeviz comments for documentation and testing purposes.
I think I _am_ noticing an increase in comment written,
but I don't think it's gotten to the point where the comments are impeding readability.
In writing these comments, I realized that I had been working under the assumption
that flowcharts (and therefore programs) all end at the same point;
however, this assumption does not hold for the implementation code:
if ever the 'executable' finds that it does not have the necessary data to generate a flowchart
(e.g., no "main" method, no Codeviz comments), the executable terminates before generating a [DOT] file.
Since "termination" can manifest itself in various ways,
it's unreasonable for Codeviz to know what termination looks like by just parsing the functional code;
so I'm currently of the opinion that the syntax should be expanded
so users can indicate when control should not flow out of particular process.
As for what the syntax looks like, I considered `//!`,
but I believe [Doxygen] uses this syntax, and I'd like to steer free of conflicts,
especially with another tool that promotes documentation; instead, I'm currently using `//X`.
As for the flowchart abstract syntax for this new thing,
I'm thinking about adding a new `FlowchartNode` named `Terminal` that extends `Process`
with the main change being that the `nextNode` is initialized to 'empty' and immutable.

As a result of this realization, I'm further realizing that each `Decision` will need to know
the last `FlowchartNode` in each of its branches to correctly generate the flowchart.
This shouldn't be terribly difficult to achieve,
but it'll take some thought to consider how best to save/retrieve that information.

Other Codeviz comments I've included in the file are `//%`
to indicate a comment that should be included on the flowchart,
and `//>` to indicate that the text in this comment
should go with the text from the previous comment.

After I finished adding/updating Codeviz comments, I added some JavaDoc to the new functions.
I half-expected to stop here as all of this refactoring took more time than I expected,
but then I looked back at the implementation plan
and realized that to stay on track I 'just' needed to add support
for rendering flowcharts with just processes (i.e., no decisions or terminals).
And this seemed simple enough to do, so I went for it.
Pretty much immediately (and I had had my doubts),
I realized that the [Graphviz Java API] I had intended to use isn't actually on Maven.
So (as maybe I should've done in the first place,)
I searched the Maven repository for Graphviz Java libraries,
and thankfully found a better library: [graphviz4j].
This library offers more support for programmatically creating flowcharts,
so I don't need to be as comfortable with DOT syntax, which is nice.

I baked the Graphviz generation functions for each node right into the class,
but I later questioned this decsision. When proposing this project,
Prof Ben mentioned that the flowchart abstract syntax would be a language in itself
such that people could use the abstract syntax when parsing a different language
or wanting to produce a flowchart with another flowchart creation language.
The former of these is functional as long as the parser is written in Java,
but it's not immediately obvious to me how I might allow people to drop in any flowchart creation language.
I think it's currently more important to me to expand the the number of nodes
than to refactor the code to be more extensible currently,
but I'll keep the concern in the back of my mind.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

How I might make flowchart creation more extensible
(i.e., separate from the flowchart abstract syntax),
and how the `Decision` implementation should change.

**What questions do you have for your critique partners? How can they best help
you?**

Any thoughts on the above or code quality?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I probably spent around 9 hours:
6 hours implementing, 3 hours reflecting.

## Post-critique summary

Matthew commented on the flowchart abstract syntax structure,
and how the relationship between nodes would affect building the flowchart from an AST.
He also offered advice on implementing the building process.

## Post-critique reflection

I haven't really considered nesting much yet
since support for some top-level structures remains to be added.
The Graphviz suggestion were really great and gave me a leg up on implementing flowchart creation,
but (as I mention above) I ended up finding a library that does most of the work for me.

[DOT]: http://www.graphviz.org/content/dot-language
[Doxygen]: http://www.stack.nl/~dimitri/doxygen/
[graphviz4j]: https://github.com/shevek/graphviz4j
[Graphviz Java API]: https://github.com/jabbalaci/graphviz-java-api
[Optional]: https://docs.oracle.com/javase/8/docs/api/java/util/Optional.html
