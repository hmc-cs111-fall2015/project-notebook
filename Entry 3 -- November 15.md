# Design notebook for week ending November 16, 2014

## Description

This week, I worked a lot on implementation. I managed to write compiling but
untested code for implementing basic state machines, including
 * Defining states
 * Write code to run on entry into a state
 * Write code to run on exit from a state
 * Write code to run in a loop while in a state
 * Write multiple of each of the above
 * Transition between states
 * Query the current state, the previous state, and the next state (in cleanup
   code)
 * Query how long they have been in a state for
 * Define interrupts: functions that get called when another function returns
   true (usually something like a bump sensor or limit switch) no matter what
   state the robot is in.

I still have things to do, though:
* Implement substates, necessary for the wait functions. This is difficult to
  implement because I don't have a great idea of what the formal specification
  for them should be. My best shot is that the wait functions should cause
  either that C++ function or that "state function" (the thing that gets called
  by the DSL) to not do anything else until th time or condition happens.  But
  this still leaves questions:
  * What if a C++ function is called from two different state functions?
  * What if there's a wait in a setup or cleanup block (arguably one of
    the most useful places to have one, since setting up may mean waiting for a
    sensor to move into position).
* Test my code. This could be done in several different ways:
  * I could just write a program in my DSL that prints out what state it's in
    and pretends to be a robot by printing out things like "I'm moving my arm
    now!". That would probably be the least effort and could show off all the
    language features easily, but is not very interesting
  * I could get one of my arduino robots working. My initial plan was to design
    my DSL just for arduino, but as I was implementing I found no need to make
    that assumption (the only place I did was that I assumed the user could
    supply a function that would return a time in milliseconds, but I'm planning
    on changing that anyway). There are two primary problems with this:
    * I would have to reconstruct a robot since none of the ones I have lying
      around are fully functional. This is not a very big deal but would take
      some time to remember how I wired it.
    * The robots I have don't have a ton of sensors, so lots of features of my
      DSL would go unused. Beyond the basic state machine, lots of features are
      for things like "I want to move my sensor into position, then take a
      measurement", but that doesn't work if the robot I'm using doesn't have
      anything that requires being moved into position.
    Beyond these problems, however, this would certainly be the coolest option,
    and I would enjoy doing it.
  * For MuddHacks, I worked with with Evan, Colin, and Daniel to make
    [t4tm](https://github.com/hexahedria/tanks-for-the-memories), a game where
    people write AIs for robots that shoot each other in-game. The AIs are
    written in python, but I could write a python library that will let AIs be
    able to be written in C++ as well, and then use my DSL.
    * This would be interesting because it has the highest probability that
      other people would use my DSL.
    * Again, it has the downside that a lot of my DSL's features would go unused
      since the inputs to the AI are easy to use. In fact, it would probably use
      _fewer_ features of my DSL because the inputs and outputs are so simple
    * It would also be less cool because it's not a physical robot

With all these in mind, I will probably do the first option to test the features
of my code, then write an interface for t4tm so that people can use my DSL, and
finally, if I have time, write a demo with a physical robot.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

The most pressing issue right now is testing. Substates will probably be useful
to users, but I'd rather get a core version of my language working before I
start adding auxiliary features. I should also be thinking in the background
about the semantics of the wait statements and how implementation of those might
work.

**What questions do you have for your critique partners? How can they best help
you?**

I have two questions for my critique partners. The first is simple if my
language looks good so far. I'd appreciate it if my partners would read my
(sample program)
[https://github.com/AdamCDunlap/StateOfTheRobot/blob/master/examples/picobot.cpp]
and tell me if the names make sense, if it would be nice to code in, and any
other features that are missing or extraneous.


**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

About 10 hours

## Post-critique summary

## Post-critique reflection
