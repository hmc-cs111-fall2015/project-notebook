# Design notebook for week ending November 2, 2014

## Description

This week, I researched and thought, essentially. The idea that I've gotten
is like this. We have some code (this code is a vague approximation of Haskell with
quasiquotes, and certainly could never run as-is):

    lhs_lambda :: Syntax -> Syntax
    lhs_lambda {f arg = exp} = {f = \arg -> exp}
    
    infer_types :: Semantics -> Semantics
    infer_types exp, env = exp, calculate_type exp env
    
    calculate_type exp@{f g}, env = env1
      where in -> out = env.type f
            env1 = env.type.set g in
            env' = env.type.set exp out
    calculate_type exp@{\x -> y}, env = exp, env'
      where env1 = calculate_type y env
            env' = env1.type.set exp (env1.type x -> env1.type y)
    
    generated = infer_types . lhs_lambda {
      square x = x * x
    }

We see here an example of mutation in `lhs_lambda`, which adds the syntactic sugar `f x = y`
to mean `f = \x -> y`, where `\x -> y` is a lambda function. Then, of type inference.
The code block is initially interpreted as an abstract syntax tree, and `lhs_lambda` applies syntactic
sugar to that. Then, the result is passed to `infer_types`, which fills in some semantic information
about types.

As far as actual implementation, it may be more straightforward
than I had imagined. Haskell's quasiquotes are relatively close to the
syntax and semantics that I had been considering. It would
still require building a lot of infrastructure.

Meanwhile, Lightweight Modular Staging in Scala is actually
spiritually fairly close to this project. It is intended
to be a way to do computations in different stages. Thus,
running a program built with LMS which outputs some kind of
code could be quite similar to my intentions. 
(The additional benefit of using LMS is that a strong
understanding of LMS might be enough to make a good
project on its own, because it is very strongly connected
to DSLs.)



## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

At the moment, the most pressing issue is what frameworks to proceed with.
One question is, can I build everything as a semi-internal DSL in Haskell?
That boils down to _how far can quasiquoting go?_
Quasiquoting is essentially a way of working with abstract syntax easily.
For example, say you have a language for doing simple numeric calculations,
and a parser called `expr`. Then,

    ast = [expr|3 + 4|]

produces the abstract syntax of the expression `3+4`. More powerfully, though,
you can use that elsewhere for pattern matching:

    eval :: Expr -> Int
    eval Number n = n
    eval [expr|$x + $y|] = (eval x) + (eval y)

This makes working with abstract syntax much nicer. The question is,
can I actually build my project entirely as a large framework built
on top of quasiquoting? I do not know.


**What questions do you have for your critique partners? How can they best help
you?**

At this time, I'm being really mean to my partner, this seems like an extremely
hard project to critique and help on. Sorry. But, I can ask this question:

Suppose I made a framework where mostly the only thing that was built-in was
a parser, an abstract syntax, and a database of some units.
If you could then easily implement compile-time unit conversions/checking
on top of that without much work, how impressive would that alone as a project
be?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

At least 8 hours. But in terms of actually writing functioning code? 0.


## Post-critique summary

The main problem here is _definitely_ being overambitious and too wide in scope.

## Post-critique reflection

The critique was very helpful on trying to focus me onto more manageable
ideas, such as something more specific to dependent types, or to
do my implementation as an extension of something else (Be it Scala,
or GCC or anything else).





