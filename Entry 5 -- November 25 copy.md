# Design notebook for week ending November 30, 2014

## Description
I didn't do much this week because it was Thanksgiving. I asked my family about potential design changes, and have some changes/questions I want to make:
  * Should there be multiple states? For example, a robot with an arm might want to be in the "move forward" state and also be in a separate "raise arm" state. This seems like it could be useful to add power, but also would make basically everything more confusing because you would have to say things like "change the arm state to x" rather than just "change state to x".
  * There really should be some way to enable/disable interrupts globally/individually or only have them enabled in some states. There should also be ways to easily communicate information back to state functions
  * A stretch goal could be to also implement a robot simulator. My test program already does a lot of this, but having a more generic thing so that pressing keys on the keyboard could act as sensors on the robot and having the system print out the current state and stuff would be really interesting and useful. Also tying this into Justis's project would be awesome, although his only works with Java.


## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I need to hook up a real robot to test things in reality.

**What questions do you have for your critique partners? How can they best help
you?**

Is having multiple states a good idea?

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Very little

## Post-critique summary
Matt made a program in my DSL and commented on how it was to use. He liked the substate design and wondered about how to do things that take time.

## Post-critique reflection
Matt's exactly right about how you do things that take time: one substate starts the process, the next waits for it to end, and the last moves on to the next task or global state. The syntax of this is somewhat worrying, though. I could define a macro that just does the `}, [] {` part, but that feels pretty weird to me.
