# Design notebook for week ending November 9, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

So after diving into the abyss that is ical4j (the library that will build
the calendars for me) I notice that they have a more basic Rules and Filter 
definition similar to my language. 

It is defined as the following:

```
Filter.setRules(rules: Rules[T][])

// then to actually filter
filter(events: Events[]): Events[]

// with the rules as a meetAll or meetAny
```

if I add in a match function to Rule, that makes it a type of rule, so they 
can be put inside one another. I could also add a Not rule into the library. 

This is so we could get something for the example:

```
calendar test {
	dates { includes(1/1/15 - 1/30/15) }

	section sub {
		dates { excludes(1/5/15 - 1/15/15) }

		section sub2 {
			dates { includes(1/7/15) }
		}
	}
}
```

Since includes can just be thought of an OR of its range and everything that has come before it,

```
Includes(prevRule: Rule, inclRange: Rule): Rule = MeetsAny([prevRule, inclRange])
```

And since excludes wants to make sure that any of the ranges that work before this rule, now cant
include this range, so it just wants to AND its not condition to the previous Rule

```
Excludes(prevRule: Rule, exclRange: Rule): Rule = MeetsAll([prevRule, NOT_RULE(exclRange))])
```

And this just requires a NOT

```
NOT_RULE(prevRule: Rule): Rule = ! prevRule.match
```

By adding in these three functions, along with a simple addition to the Filter class, I think 
the ability to nest conditions is entirely possible. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

**What questions do you have for your critique partners? How can they best help
you?**

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

## Post-critique summary

## Post-critique reflection
