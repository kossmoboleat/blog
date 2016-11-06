---
layout: post
title: New Software Smell
date: 2016-02-23 22:35:45.000000000 +01:00
---
Preparing our apartment for an infant, we‘ve renovated and started to move stuff around to make room. It turns out such a small human needs much more utensils and a surprisingly large selection of clothes, which I‘ve been told we‘ll have to replace in 3 months. To make matters easier, I‘ve ordered a lot of stuff online. Because of Amazon‘s questionable minimum 29 € order for free shipping, we‘ve also shipped a few very debatable items like sponges. Then instead of sending a single parcel Amazon of course decided to send 3 parcels. Still receiving these small neatly packed boxes with new gadgets always feels a bit like receiving gifts.



The many unboxing videos on youtube show that I‘m not alone in this. Especially with electronics this fetish is very strong. My smartphone arrived in a nice small red parcel that contained small boxes with the charging cable, the adapter and other knick-knacks. Everything was intricately designed to elicit exactly this emotional response. The new car smell is another example of a means to reward you for buying new stuff instead of getting it rarely used off eBay instead. With smartphones newness is even more important because any device is already outdated after a year.

# OS nirvana

When you get a new computer it‘s very much the same. This is your new fast machine, never touched by any other human, except maybe some underpaid Chinese laborer. And then the operating system on the machine is still in its pristine new shape. Back when Windows degraded very noticeably you could only reach this neat nirvana by reinstalling your OS and then again everything was so fast!



When you tinker with on a software project for a while, you start noticing hairline cracks in your architecture and some dirty code lying around in some dark seldomly used component. How nice would it be to throw all this old muck out and start fresh! Also if the software has gotten a bit old, what about the people behind it? They too must be a bit old-fashioned, pre-disposed to carry on the legacy instead of breaking out to start a new adventure. Now the analogy breaks down a bit because the big pile of code lying around is not rusting, it‘s used all the time and it‘s doing a lot of useful stuff for many people. The new shiny code that still smells like fresh spring water, hasn‘t aged at all yet. It hasn‘t experienced that first brutal onslaught of the hordes of users yet.


From time to time it‘s useful to program something small for fun besides work. Then you‘ll see how slow you‘re going with your big project but you‘ll have much more clarity and structure and you‘ll want to bring this to your work project too. Your quest becomes the search for repetition that‘s gotten out of hand and replace it with powerful shorter code. Or rethink your architecture assumptions and slim your code to make it fast and clear again. Every time you manage to reduce the size of your code base without compromising on the speed, function or useful extensibility of your code, you close one of those hairline cracks.

# schizophrenic evil twin brothers

Of course it‘s not such a great idea to run around like a [headless chicken](https://en.wikipedia.org/wiki/Mike_the_Headless_Chicken) and change code everywhere. First make sure you‘ve exactly understood what the code is doing that you‘re changing. Reading it all very attentively is one way to do this and the other is testing. Testing puts you in the shoes of your [evil twin brother](https://en.wikipedia.org/wiki/Treehouse_of_Horror_VII#.22The_Thing_and_I.22) that‘s always trying to destroy your work. With a little schizophrenic streak you will try your best to make the code break. When you can‘t find another behavior to break, you are confident that any refactoring you make isn‘t going to break anything. Now you can safely make the code really nice. That‘s the real emotional payoff for testing. It‘s also the basis for the excellent book „Working with Legacy Code“ by Michael Feathers.


Consequently if you want to change something, you should have tested it: Ok, fine. That means you should have tested most of your code, otherwise how can you know that you broke it. Think of the time when you changed that famous piece of code that could never have made that machine crash in production. To get a nice high coverage you will have to test a lot, so you want tests that are the fastest to write, help you find errors easily, can cover all of your code and they should run quickly too, because you don‘t want to wait a whole lot of time for all the test code everybody has written now. That thins your choices down to unit tests. Otherwise you won‘t be able to test all of the fantistillion exponential combinations of different states and parameters that your code splits up deeper in the stack.

# Kessel sprint

Michael Feathers also has some advice how to choose your new refactored code‘s design. Visualize the result and imagine what it should look like. Something Rick Hickley coined [„Hammock-Driven-Design“](https://www.youtube.com/watch?v=f84n5oFoZBc), which can devolve in TDD on the smaller scale then. With some of these techniques and an unwavering desire to make things better even old legacy bearers can succeed. Working on "used" code doesn't have to feel like Sisyphus work. Think rather like MacGyver, doing your best with what you have, or Han Solo and Chewie fixing their old Millenium Falcon to make the [Kessel Run](http://starwars.wikia.com/wiki/Kessel_Run) in less than 12 parsecs. Let's try to make it fly again for the next sprint.
