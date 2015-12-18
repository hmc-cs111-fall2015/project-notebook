# Design notebook for week ending November 23, 2014

## Description

This week, I mainly tested and debugged my implementation. I also thought a lot
about how to implement substates and came up with a solution that I think is
pretty good. Basically, multiple functions are passed to the `state_func` macro
which act as substate functions, and the user can move between these substates
easily. Each different call to `state_func` contains its own substates, so lots
of combinations are possible.

Now the most relevant example is in `examples/printtest.cpp`, which emulations
robot actions with print statements and sensors with button presses inside
ncurses. I think it's a pretty good test that tests most features.

The only feature I know of that doesn't work right now is the `every` block,
which should run a piece of code every so often with the given time. I just have
to debug it and haven't gotten around to that.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue right now is that I need to implement a back end so that
I can run user tests.

**What questions do you have for your critique partners? How can they best help
you?**

I want someone to try to use my DSL sometime soon, but I think that I need a
good back end to be able to get good feedback from that, and I don't have that
yet. For my critique parter, reading over the documentation, trying to
implement something simple with a pretend robot back end, and giving me comments
would be really useful.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I'm really not sure about exact numbers because I worked a lot on my project in
small increments throughout the week. I certainly spent significant time on it,
though.

## Post-critique summary/reflection
From my critique, I learned that my example code was not clear enough. With that
I decided to leave things in the examples directory as tests but also write
better documentation in the readme that contains simple examples that are more
informative.
