# Design notebook for week ending November 2, 2014

## Description

I spent a lot of time this week reading about traditional multiple dispatch systems
and thinking about how I can apply them to my project.  Typically such systems are
used to handle different types of inputs in dynamically typed languages.  The main 
examples I saw were things like this

```python
def add(first, second):
    if isinstance(first, int) and isinstance(second, int):
        return first + second
    else:
        ...
        
# vs

@dispatch(int, int)
def add(first, second):
    return first + second
    
@dispatch(objecct, object)
def add(first, second):
    return "{}{}".format(first, second)
```

While this is a contrived example, it allows for the simplification of the actual
functions and delegates the process to some dispatching function (which is in 
this case a decorator).  I plan on using a similar idea in my language.  It 
will involve (at least) 2 decorators:

1. `@register_reaction_mechanism`
2. `@register_molecule_structure`
 
Each of these decorators will be part of the multiple dispatch system.  It will
have to dispatch based on the reaction mechanism, as well as how the underlying
data is being represented.  

#### `register_reaction_mechanism(mechanism_name, requirements=None, moleculeType=None)`
This decorator should be applied to a function (or callable class - I haven't
decided which is preferred yet).  It could look like this

```python
@register_reaction_mechanism(
    'Diels Alder Reaction', 
    requirements={'heat': heat(.5), 'light': light(.5), 'resonance': resonance(1)})
def diels_alder_mechanism(reactants, conditions):
    ...
```

The decorator will take a string (the name of the mechanism, used in verbose 
output mode as well as the key in the dictionary the dispatch system will use)
and then an optional dicitonary of requirements that maps from strings to functions.
Each of these functions will probably have a mapping somewhat like this:

```
function A(*args, **kwargs) -> (function B(reactants, conditions) -> Score)
```

In this case, each of `heat`, `light`, and `resonance` take floating point values
that represent the "importance" of that requirement - in this case resonance
is an absolute must, while heat and light are both preferred.  They then return
functions closing over those input arguments that will result in some `Score` being
returned.  This will probably be a `float`, or potential a custom object that is
essentially a light wrapper for a `float`.  The idea is that score will determine where
in the dispatch system this mechanism falls (i.e. how likely it is that this 
mechanism will be attempted).

A user will attempt a reaction as follows:

```python
hydronium = load_molecule(source)
hydroxide = load_molecule(source)
products = react([hydronium, hydroxide], conditions)
```

The dispatch system will analyze the reactants `[hydronium, hydroxide]` as well as 
the `conditions` and attempt to score each reaction mechanism based on the provided
and computed information.  It will then provide some sort of partial order and try
to find a reaction that will yield a result.

It also takes an optional argument for the type of the molecule.  This isn't used
to determine the score, but rather if a conversion between my implementation of 
the molecular data structure and some user-defined one is necessary.  For example,
in the "Diels-Alder" reaction I specified above there are a number of very important,
very low-level considerations needed that my data structure will probably not take
into consideration.  Thus the user may define (and register) their own data type
that also quacks like a duck (i.e. is equivalent in terms of duck typing) and 
specify that it should be used to conduct this reaction.

#### `register_molecule_structure(name="from_default")`
This is the decorator used for that purpose.  It should decorate a class.

```python
@register_molecule_structure()
class DielsAlderStructure(object):
    
    @classmethod 
    def from_default(cls, molecule):
        ...
        
    def __init__(self, *args, **kwargs):
        ...
```

This is the general format of such a structure.  It must define a class method
named `from_default` (or whatever is specified in the argument to the decorator)
that can construct this data structure from my implementation of a molecule. 
Other than that it should be duck-type equivalent (at least for any operations
they wish to do on it), which I haven't completely worked out yet.

Between these two decorators and a sufficiently powerful and well-engineered 
dispatch system, this language should be very flexible and easy to extend. I do
have a few concerns:

1. Slowness of dispatch system
2. What happens if no match is found
3. What happens if the wrong match is found
4. What happens if the user knows what kind of mechanism should occur, but not
the specifics of the result?
5. What happens if the user wants to work backwards from a product to some 
other material, and wants to know the steps that needed to be taken to get there?

I have ideas for some of them:

1. This will just have to rely on good algorithm design and "fast-enough", otherwise
use CFFI, SWIG, Cython, or C-extensions for the mission-critical parts.
2. This should be an error of some kind
3. I don't know how to detect this unless users file bug reports.
4. Ideally `react` could have some optional keyword argument to specify the first
type of reaction to be tried.
5. This is called retrosynthesis, and will be out of scope for this class's project.

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

Designing the dispatch system.  I need to set things up such that registering
new mechanisms works well (first priority) and then that registering new
data structures works well (second priority).  Once I've implemented this I
think the rest should be fairly straightforward.

**What questions do you have for your critique partners? How can they best help
you?**

Please let me know if any of the technical Chemistry details don't make sense 
or don't help my explanations.  Also, if you have any input about how I should
go about designing my dispatch system please let me know.  At this point it is
still a very fragile idea.

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

Around 9 hours.  Most of that was reading about typical multiple-dispatch as well
as sketching out implementation plans for how I can do dispatch.  None of that 
is in a repository (none of it has even been coded) because I'm still playing around
with it.

## Post-critique summary

## Post-critique reflection
