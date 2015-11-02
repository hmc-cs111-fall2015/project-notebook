# Design notebook for week ending November 2, 2014

## Description

**TODO:** Fill in this part with information about your work this week:
important design decisions, changes to previous decisions, open questions,
exciting milestones, preliminary results, etc. Feel free to include images
(e.g., a sketch of the design or a screenshot of a running program), links to
code, and any other resources that you think will help clearly convey your
design process.

My main task this week was to better research the output of my language. Since
I hope to output an icalendar file, I looked up Java libraries for building 
calendars in this format. The best one I could find is called [ical4j](https://github.com/ical4j/ical4j). 
While it has much more functionality than
I will use, it seems to be the most reliable library. This should allow me to
spend more time building the language than debugging or fixing the library. 

Another concern was dealing with different time zones, but this library seems 
to deal with them, so that should make it easier to allow users to change them. 

As my initial idea for syntax aligns decently well with the syntax my team
used for our external piconot, I have decided to use Scala as the host 
language to my external DSL. Here is the initial concept of the DSL:


```
calendar school-calendar{
	
	dates {
		includes { 9/1/15 - 12/17/15 }
		excludes { 	10/15/15 - 10/18/15,
					11/25/15 - 11/28/15 }
	}

	section classes {

		dates {
			excludes { 12/9/15 - 12/17/15 }
		}

		event math {
			times { 10:00am - 11:00am MW}
			priority: high
		}

		event physics {
			times {	11:00am - 12:00pm MW,
					9:00am - 9:50am T }
		}
	}

	section finals {
		dates {
			excludes { 9/1/15 - 12/9/15 }
		}

		...
	}
}
```

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
