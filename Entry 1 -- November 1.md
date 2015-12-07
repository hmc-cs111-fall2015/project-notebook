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
calendar school-calendar {
	
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

A large part of this project, I hope, will be allowing for templating of calendars.
A problem I see currently with this is that we dont have an easy way of associating 
different times to different sections, but have an event be in both sections without
writing it. I plan on working on more design decisions for future proofing stuff
like this in the following week. One idea I am working on is having sections work
as a sort of tag. When an event uses that tag, that tag is assumed to be copied 
inside of that section, so if the event "math" had a tag for finals and a tag for 
classes, but was outside of both of them, it would be assumed that it truly under
both of them.

The only problem I have with this idea is that its not as "clean" as just having
scoped objects. The language would have to precompute all posible sections before
evaluating events. 

I feel like this is pretty far in the future though, as this next week will be mostly
implementing an API wrapper of the icalendar library, making it easier to call from
my DSL. I will focus on the wrapper having a way to repeat over a time period, 
so that the code the interpreter doesn't have to do as much of the dirty work. 

## Questions

**What is the most pressing issue for your project? What design decision do
you need to make, what implementation issue are you trying to solve, or how
are you evaluating your design and implementation?**

I guess a bit decision to make would be to decide how much freedom the user
should have. Since this is a DSL based around removing constraints, I am 
leaning towards the side of total freedom, but I guess time will tell if 
this is the wrong choice. 

I think it would be best to just start to write it, as I feel like I have a 
pretty concrete idea of what I want this language to achieve. After some 
experimenting, maybe new ideas will come out. 

**What questions do you have for your critique partners? How can they best help
you?**

I guess thinking of use cases other than the ones I have presented would be
the most helpful thing right now. Since the syntax and partially the semantics
are being designed around the use cases, the more there are, the better the
language will be. 

**How much time did you spend on the project this week? If you're working in a
team, how did you share the labor?**

I did a lot of research into icalendar and libraries that implement it. I
would say I worked for 8 hours outside of class this week. 

## Post-critique summary

## Post-critique reflection
