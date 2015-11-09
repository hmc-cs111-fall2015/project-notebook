# Design notebook for week ending November 1, 2015

## Description

I spent a lot of time this week thinking about what kind of logic structures
robot programmers want and what kind of things programmers would find useful.
I'm mostly sure that the only thing that's really helpful is a state machine
construct. There should be things like time since last state change, a list of
previous states, and easy ways to store previous sensor readings. This makes me
worried that my project will be too short, though. If I'm just adding a state
machine construct, will it be too small to be a good DSL and would be better off
as just an API? I'm still struggling with this and I'm somewhat worried. Next
week I should write some example programs and see what other features would be
useful.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I'm most worried about this project being too small. 

**What questions do you have for your critique partners? How can they best help
you?**

Does this really seem appropriate for a DSL or is some sort of API a better
approach?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

5 hours
