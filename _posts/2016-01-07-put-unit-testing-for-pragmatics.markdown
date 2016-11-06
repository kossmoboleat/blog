---
layout: post
title: Pragmatically Tested
date: 2016-01-07 22:35:14.000000000 +01:00
---
Jeff Langr has written a great little book about unit testing called ["Pragmatic Unit Testing in Java 8 with JUnit"](https://pragprog.com/book/utj2/pragmatic-unit-testing-in-java-8-with-junit). It's actually the newest edition of a book that was first written in 2003 and aimed to describe the most basic tools a developer needs for the excellent [pragmatic bookshelf](https://pragprog.com/) - the others were version control and automated builds. Of course by now any seasoned developer knows what unit testing is about, but this book still makes many good points and gives you some tips how to write your tests.

## Warmup

The first chapters are predictable enough with some basic setup instructions and some first examples. Some JUnit specifics are touched on too and the more expressive hamcrest matchers are introduced. Then come the juicy parts. Tests with given-when-then or arrange-act-assert structure are presented, the importance of naming the tests consistently with meaningful names and using tests as living documentation.

## Donkeys on Bridges

The part I like most about this book comes in part two in the form of some mnemnomics - "Eselsbrücken" in German for the rest of who weren't born with unit testing super powers. I'll list them here to show you how well this worked for me - No cheating, I swear!

FIRST stands for how desirable test properties

* [F]ast test execution
* [I]solated tests - no data dependencies (say hello to my favorite test hotels on Majorca or Fuerte Ventura) and fixed test order
* [R]epeatable - tests should always be runnable and give the same result every time
* [S]elf-Validating - craft them with useful assertions/error messages that show what's wrong right away
* [T]imely - when you write the tests soon after or even before coding it will be much less of a hassle than in a few days

Right-BICEP describes what you should test

* Right - have some tests for the happy path behavior
* [B]oundary Conditions - write _one_ test for every boundary condition
* [I]nverse Relation - check what happens if methods are called in a different order
* [C]ross-Check results with other sources of truth if in doubt
* [E]rror conditions - make sure you cover all the cases that will make the code fail
* [P]erformance - test performance critical code correctly with enough executions. I would suggest the standard tool [jmh](http://openjdk.java.net/projects/code-tools/jmh/).

How to test boundary conditions CORRECTly:

* [C]onformance test that different manifestations of a pattern are correctly recognized, e.g. regular expressions
* [O]rdering - check that a very different ordering/sorting of input is handled correctly
* [R]ange - test the extreme points of the relevant type. The author then suggests using enums and classes instead of these primitive types to reduce the change for errors.
* [R]eference - make sure the state or objects your code references are reasonable and that it doesn't explode if that's not the case.
* [E]xistence - be sure that nothing disastrous happens with null or empty parameters.
* [C]ardinality - vary the number of objects in your collections/arrays, test for empty, one and many elements.
* [T]ime - think timezones, extreme time spans, interval problems etc.

## Make it testable

The author gives some basic examples on how to whip an untestable code base into shape, but Michael Feathers ["Working Effectively with Legacy Code"](http://www.pearsonhighered.com/educator/product/Working-Effectively-with-Legacy-Code/9780131177055.page) does this much better. The book shows you the "absolute minimal, safest changes to the code Péter Török put it on [stackoverflow](http://programmers.stackexchange.com/questions/122014/what-are-the-key-points-of-working-effectively-with-legacy-code). That book gives you all the gory details too, but Jeff Langr gives a nice appetizer that's much easier to follow.

Mocks using the library Mockito are also introduced and explained in sufficient detail to cover the basic use cases.

## Wrap it up

To put things in perspective TDD is touched on and also continuous integration and code coverage, which is not that great btw - [see this paper (PDF)](https://cs.uwaterloo.ca/~rtholmes/papers/icse_2014_inozemtseva.pdf). In our current team we're trying to push for much better unit tests and I agree with the pragmatic advice on how to introduce unit testing in this book, which I wish I had presented as well in my team, too. Regarding standards he writes "Start minimally [..] Seed a bit of discussion, run a quick meeting, and put into writing the expectations for the team". We've started the process and have something workable soon, I hope.

