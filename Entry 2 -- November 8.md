# Design notebook for week ending November 8, 2015

## Description

I spent a good amount of time figuring out how to use [Maven]
because I didn't want to deal with manually downloading
and managing every external library I want to use.
After I finally figured it out, I gained access to [JavaParser]
so I started working on my proof of concept for parsing Java comments.
JavaParser provides a function for extracting every comment from a file,
so I just used that. The parser also assigns comments to nodes in the AST
that represent functional Java syntax. For example,
if there's a line comment immediately preceding a variable declaration,
then the abstract syntax node representing the variable declaration
contains a reference to the comment; similarly,
the comment contains a reference to the node to which it refers.
One of these could prove useful in the future.

After I finished the proof of concept, I started developing a flowchart abstract syntax. My first iteration looked like this (using pseudo Haskell/Java):

```haskell
typedef Flowchart = LinkedList<Node>
data Node = Process {description :: String}
          | Decision {condition :: String, trueBranch :: Flowchart, falseBranch :: Flowchart}
```

When I ran the model by Prof Ben, he recomended just making a `Flowchart` a sort of pointer to the first `Node` and then have each `Node` reference the next `Node`, which I think is mainly more space efficient. Then the new abstract syntax is essentially:

```java
abstract class Node {
    @Nullable Node nextNode;
}

class Process extends Node {
    String description;
}

class Decision extends Node {
    String condition;
    Node trueBranch;
    Node falseBranch;
}
```

Notice that `nextNode` is optional so that the last `Node` in the flowchart
simply doesn't refer to a `nextNode`. Shortly after writing the initial classes
for each of these components, I realized that I'd want dynamic typing
when using this abstract syntax to generate a flowchart
since I wouldn't have any immediate information about what _concrete_ type each `nextNode` is.
To get dynamic typing in Java, I'd need to use the [Visitor pattern],
which does not sound at all like fun. After doing a little bit of searching
for a Scala-implemented Java parser, I realized that Scala can use Java libraries,
which means I think I can transition the host language from Java to Scala,
still use JavaParser, and gain the benefits of dynamic typing via pattern matching.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue is confirming whether I _really_ need dynamic typing
(I'm fairly certain I do); and based on this decision,
whether I want to change the host language to Scala,
which should be fairly easy to do at such an early stage in development.

**What questions do you have for your critique partners? How can they best help
you?**

Take a look at the proposed flowchart abstract syntaxes, and lend me your thoughts.
Also am I missing anything concerning the dynamic typing issue?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I honestly probably spent much more time on the project than I should have. :sweat_smile:
I spent 2 hours on responding to my critique,
7 hours 'implementing' (most of this time was spent researching Maven and reading files in Java),
2 hours on the language design and implementation assignment,
and 1 hour updating the notebook.

## Post-critique summary

## Post-critique reflection

[JavaParser]: http://javaparser.github.io/javaparser/
[Maven]: https://maven.apache.org/what-is-maven.html
[Visitor pattern]: https://en.wikipedia.org/wiki/Visitor_pattern
