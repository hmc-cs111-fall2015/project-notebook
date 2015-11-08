# Design notebook for week ending November 9, 2014

## Description
 * I spent a lot of time researching how to print out an enum as a string in C++. I found ways to do it but they required defining them in weird ways such as `#define SEQ (_INVALID_)(GoForward)(GoBack)(TurnLeft)`, or doing the enum to string conversion at runtime which takes time linear in the number of elements in the enum. I think I'll avoid doing all of this, and it will be a future expansion for an external DSL

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

 * How much preprocessor magic should I do and how much should I stick with easy-to-understand behavior?
   * e.g. to define states I could do `DefineStates(TurnLeft, TurnRight);` or I could make them do `enum class States{ TurnLeft, TurnRight }; DefineStates<States>();` The first looks nicer but may be harder for someone to parse into C++, the second one makes it more obvious what C++ is doing
     * For this example, I don't think I need to specifically say `DefineStates` so I'll leave it as the first
   * Since I'm trying to get more DSL-y than API-y, I'll stick with the first for now

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary

## Post-critique reflection
