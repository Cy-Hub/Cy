Cy
==

*OBSOLETE:*  This repo is of historical interest only. The line of thought continues in [the World
 Wide Hack project](https://github.com/WorldWideHack).

Cy (pronounced like "sigh") is a development environment for the World Wide Hack -- a worldwide collaborative search through the space of useful software components. It is an effort to re-imagine the craft of programming, with
inspiration from Bret Victor's [Learnable Programming](http://worrydream.com/LearnableProgramming/), and
with a focus on frictionless collaboration.

Cy's design focuses on four of the most important new programming problems during its intended
prime of life -- the 2020s: 

* ubiquitous computing,
* gestural interfaces, 
* augmented reality including virtual reality and telepresence,
* massive parallelism.

These are the problems of writing code that lives in the world instead of behind a keyboard and monitor.
We desperately need better programming paradigms and tools for this because right now only a tiny number
of expert programmers with special skills can do it. Our lives were transformed when web technologies
enabled millions of people to write useful code behind a keyboard and monitor. Now we have to enable
millions of people with varied skills and interests to write code that lives in the world.

Cy was created by Dean Thompson.

Language Platform
-----------------

Cy could be based on [the Wolfram Language](https://www.wolfram.com/language/), [Rust](http://rust-lang.org), or a combination of two. (Or perhaps there is a better choice than either.) The Wolfram Language is intriguing for Cy because it is especially amenable to learnable programming:

* Mathematica's existing "notebook" interface already has some of the characteristics of learnable programming, such as easy interactive exploration in the style of SmallTalk or LISP, with immediate access to graphics and data visualization.
* Because in the Wolfram Language (like LISP), programs are also data structures in the language, it is relatively straightforward to build powerful programming tools in the direction Cy envisions.
* The functional style of the Wolfram Language, plus the rich library of existing well-defined functions, lend themselves to highly composable abstractions.

Cy is based on Mozilla's new language  Rust is intriguing for Cy because it
combines pragmatism with a powerful type system and other powerful safety features, and because it compiles
through [LLVM](http://llvm.org).

One sensible approach, if both the Wolfram Language and Rust are successful, would be to embrace both, with Wolfram Language as the high-level programming environment and Rust for building libraries that need to live closer to the metal.


The World Wide Hack
-------------------

The World Wide Hack is a collaborative search through the space of useful software components by
people and machines who take on the following five roles:

- *Principal*: the primary author of a particular set of software components.

- *Peer*: creates software and information for his own purposes, but that may be useful to the
   Principal. (A Peer acts as a Principal from the perspective of his own projects.)

- *Freelancer*: assists the Principal in a "work for hire" capacity, such as by coding to a spec or
   generating test cases. (A Freelancer acts as a Principal from the perspective of the tasks that
   he takes on.)

- *Random*: a member of the crowd, which takes on tasks such as certain kinds of testing that do not
   require the attention of a Principal.

- *Machine Assistant* (MA): a software component that takes on tasks such as coding to a spec or
   generating test cases.

The Cy development environment facilitates each of these five roles and the flow among them. The
goal is a seamless interplay across creation, discovery, and validation, and among highly skilled
Principals, relatively unskilled Randoms, and sophisticated but mechanical MAs.

For example, a Principal needs a UI component for creating a to-do item. She begins writing some
high-level documentation for this component. An MA integrated into her IDE suggests an open source
component (written by a Peer) with documentation textually similar to what the Principal has written
so far, and with quality scores and open-source license that meet the Principal's filters. The
Principal examines the open source component and decides that although it doesn't perfectly fit her
needs, it is a good starting point. She clones the component, edits its documentation to describe a
variation that she wants, flags it as needing assistance with 3 assistance value points, and moves
on to something else. (She doesn't change the 12-hour deadline that she uses as her default for
assistance.)

A Freelancer who has worked with the original component before and who meets the Principal's
freelance reputation filter (and whose principal reputation filter was met by the Principal), is
alerted to this request. He checks the fee for the work (which was computed automatically from the
Principal's monthly budget, her assistance-value-point velocity, and the value points that she
assigned to this task) and decides it is worth his while. He claims the assistance flag. (This
Principal pays cash and this Freelancer prefers cash. Most work-for-hire deals are done in-kind on
Cy credits.)

The Freelancer creates a new version of the component that he believes matches its new
documentation, adds some entries to the new version's human-testing plan, and releases the
assistance flag. An MA notices that both the component and the human-testing plan have been
modified since the component was last tested, that the component has an unclaimed assistance flag,
and that the Principal has a cash budget. It creates a set of crowd-sourcing tasks to test the
modified component against the modified human-testing plan. These tasks are carried out by Randoms,
with multiple Randoms being assigned the same testing tasks so that the results can be
cross-checked. The level of redundancy depends on the reputations of the Randoms who do the work.

The Principal is alerted that the modified component is ready for her review. She examines the
diffs from the original, the updates to the human-testing plan, and the summarized test reports from
the Randoms. She accepts the work, which is then incorporated into her project. This triggers
payments to the Freelancer and the Randoms.

The Peer who created the original version of the component is alerted that a new version has been
implemented and tested. He sees that the Principal's open-source license allows him to incorporate
the changes, and he likes them, so he incorporates them into his own version.


IDE for the World Wide Hack
---------------------------

One reasonable way of looking at Cy is to see it as a development environment that is driven by the
goals of first realizing Bret Victor's vision of Learnable Programming and then leveraging the
resulting benefits. Cy is also inspired partly by Chris Granger's [Light
Table](http://www.chris-granger.com/2012/04/12/light-table---a-new-ide-concept/) project.

Cy's IDE will apply Bret's ideas about "creating by reacting" and "recomposition" by automatically
pulling in open-source code examples that meet the developer's needs, much as chess software pulls
in examples of public games that proceeded from the current position. Machine Assistants (MAs)
integrated into the IDE will find or generate code to meet the developer's needs, much as chess
software shows potential lines of play and their likely outcomes. For example, when the developer
starts writing a signature and contract for a function, an MA will suggest existing functions in
open-source code that have similar signatures and contracts. It will decorate each suggested
function with its quality score and the developer's reputation and achievement scores.

An MA will even suggest implementations of the function that combine small numbers of existing
functions to provide the specified signature and meet the contract. The developer can navigate to
examples in public source code that have combined those functions in that way. The intended feel is
much like how chess software shows references to published games that have proceeded from the
current board position or from a potential line of play.


Platform Design
---------------

Cy will provide the environment, data, and workflow needed to support the World Wide Hack:

- Reputation management and quality scoring.
- Freelancing and crowd-sourcing.
- Micropayments.
- API contracts and testing.
- Publishing, versioning, and dependency management.
- Open-source license management.
- Searching for components and functions that work in a particular context.
- Human-readable data (all types have readable JSON representations).
- Development-mode capture and playback of component and function inputs and outputs.
- Built-in tracing and debugging integrated with API contracts.
- Production deployment.


License
-------

All artifacts in this project (whether so marked or not) are Copyright (c) Dean Thompson and
MIT licensed.


Documentation
-------------

See the doc and notes directories for documentation work-in-progress. Also see the Cy directory
for examples.
