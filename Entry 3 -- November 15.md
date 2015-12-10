# Design notebook for week ending November 16, 2014

## Description

###11/11/15

12:45-2:30p

While building the parser, I realized my AST needs to be changed.

Map files are made of:
* Tile specifications
* Map specifications
* 0 or more generate calls, for either normal or debug maps

So the AST should reflect this, and it would make parsing much easier.
The AST, then, would have:
* A map of `tileName`s to `Tile`/`Freetile` objects
* <s>A list of `Map` objects</s> One `Map` object
* A list of Generate calls

The `tilemap` object, which is the equivalent of the `runner` object in the Piconot assignment, will then return an AST, which, depending on the generate call list, will call the generateMap functions from `semantics.scala`

Things that need to be changed/done:
* Change the IR to handle this AST
  * `Map`s no longer have names
  * `Layer`s and `Area`s no longer deal with `Tile` objects; instead, `Area`s have a `TileName`, and `Layer`s have lists of `TileName`s and `Point`s
  * Add the AST itself, with a tileTable mapping `TileName`s to `Tile` objects**
* Continue writing the parser, making updates as needed to the IR
* Fix semantics to look up the tiles in the tileTable rather than digging out the `Tile`s from the `Layer`s
* Write the `tilemap` code

** To handle this, there are now BasicTiles and FreeTiles that both extend from a Tile class that has the value name, as this is the only shared val between them.

I've changed the IR; `AST`s have the table described above, a map object, and a list of (`MapType`, `String`), where `MapType` is either `basic` or `debug` and the `String` is the name of the output file the map will be saved as.

Parsing is making it nearly impossible to return a HashMap, which makes some sense.
Instead, add to IR a `tileTable` object that turns a list of (Tilename, Tile) into that HashMap
That way, the parser only has to deal with lists.

+15 minutes

9:00-11:30p

Most of the parser is in place. Minor changes to the ir were made (`Area`s and `PlacePoint`s are now both things that inherit from `Instr`, so that a list of `Instr`s can be parsed).

The parsers are cooperative for the most part, but now I'm getting strange errors when trying to use the "rword" parser in the `layer` and `originKeyword` parsers.

Especially on `originKeyword`;

`ident ^^^ topLeft` lets things work fine; `topLeft` is recognized as an `Origin`.
I also tried using `rword("bottomLeft")`, and that didn't work.
However, what's really strange is that
```
"bottomLeft" ^^^ bottomLeft
      | rword("topLeft" ^^^ topLeft
```

specifically without the closing `)` will let `bottomleft` be recognized just fine.
As soon as the `)` is added in, that line errors and the syntax highlighting stops working.

###11/14/15

10-11a

Fixed part of semantics; it now has a loadAST function that will generate the proper amount of maps automatically.

12:10-1:10p

Originally, I was handling sorting the layers in semantics, but instead I ended up writing a simple mergesort function, moved it over to IR, and put it in the map class. Now, when maps are initialized, the list of layers is sorted on the spot, and errors can occur right then if two layers have the same precedence.

The instrs will also be sorted, with fill instructions before any place instructions

###11/14/15

11:15-1:15a

Silly mistake: wholeNumber produces a num, but I needed to use num.toInt to make it work.
This made the entire parser work.

Now, most things are implemented. Filling areas isn't set up, but all of the parsing and AST are.
Semantics needs to handle filling areas, as well as debug maps.
Placing tiles is implemented.

The tilemap object is set up, but not quite working.
Basically, I need to find out how to make something that people can call to write and run the code.

###11/15/15

1:45-2:30p

Tilemap.scala doesn't give any warnings in Eclipse, but refuses to compile.
At `freetyle.parsing.parser`, it says it doesn't know what `freetyle` is.

I'm going to make some tiles instead, since I need to anyways.

+2 hours

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

How to get things to run from the command line.

**What questions do you have for your critique partners? How can they best help
you?**

??? The next thing to think about is probably what kinds of shapes should be included for filling in. Just rectangles and freeform shapes?
Circles are probably far too difficult for this project.

**How much time did you spend on the project this week?**

~11 hours 15 minutes

## Post-critique summary

## Post-critique reflection
