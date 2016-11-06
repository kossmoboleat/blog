---
layout: post
title: Taming the Parentheses - Get Started With Clojure
date: 2016-10-13 10:40:17.000000000 +02:00
---
## (like-parentheses?)

The first big difference of Clojure to C-style languages like Java and Javascript are the parentheses. To some they seem overly abundant, although the style is not *that* different.

```python
println("hello world")
```

is valid Python 3 while Clojure has

```clojure
(println "hello world")
```

Clojure now goes one step further and applies the same principle to almost anything like e.g. function declaration:

```clojure
(defn fun [param]
  "result")
```

## (watch talk)

To get a better sense if Clojure is for you, I suggest watching the excellent talk [Clojure, made simple](https://www.youtube.com/watch?v=VSdnJDO-xdg) by the language creator Rich Hickey.

At my company I've held a Clojure talk recently too and tried to give an overview of the language and present its applications in web development. Of course without a video you miss out on the demos but it might be worth to skip through quickly anyway: [Clojure - The Average Joe's Lisp](https://kossmoboleat.github.io/clojure_intro).

My goal was to show that Clojure is far from the stereotype of an academic esoteric language and can be learned easily to elegantly solve real-world problems.

Some other people have also taken a stab at this. The clean-code guru Robert Martin aka Uncle Bob have written about how they like Clojure:
[Clojure Is the New C](https://www.infoq.com/presentations/clojure-c), [Why Clojure?](http://thecleancoder.blogspot.de/2010/08/why-clojure.html)

## (try)

If you want to dive right in and write code, try the online interpreter (or [REPL](https://en.wikipedia.org/wiki/Read%E2%80%93eval%E2%80%93print_loop)) [tryclj.com](http://www.tryclj.com/) or solve one of the easy beginner problems like finding the greatest common divisor with another interactive site [4clojure.com](http://www.4clojure.com/problem/66) (you can also pick an easier one like [this](http://www.4clojure.com/problem/14)). In a similar vein the katas from [codewars.com](https://www.codewars.com) helped me get into the language (and become fluent in it).

When you're ready to write some larger programs of your own I suggest you install a [JDK](http://www.oracle.com/technetwork/java/javase/downloads/index.html) and then the basic build tool [Leinigen](http://leiningen.org/). Here's how to do it on unixy OSs (go to the website for Windows instructions):

```shell
$ wget https://raw.githubusercontent.com/technomancy/leiningen/stable/bin/lein
# move if in a dir on your $PATH, like ~/bin
$ mv lein ~/bin
# make it executable
$ chmod a+x ~/bin/lein
# run it once to self-install
$ lein
```

To edit files I like the excellent [cursive](https://cursive-ide.com/) plugin for IntelliJ (community edition is fine) or [Light Table](http://lighttable.com/) if you're not a big IDE fan.

As a starting point for web development I suggest the [Luminus](http://www.luminusweb.net/) micro-framework which packs the best web libraries in one nice template a bit like [JHipster](https://jhipster.github.io/) generates a nice [Spring Boot](https://projects.spring.io/spring-boot/) + AngularJS project. Just type this in a terminal:

```shell
$ lein new luminus my-app
$ cd my-app
$ lein run
Started server on port 3000
```

Although I'm skeptical of large frameworks the [Arachne](http://arachne-framework.org/) is made by very knowledgeable web developers and will hopefully come out soon and not turn web development into plumbing of some magical components.

## (read)

If you come this far, take a look at some of the excellent books on Clojure:

- [Programming Clojure by Stuart Halloway](https://pragprog.com/book/shcloj/programming-clojure)
- [Web Development with Clojure by Dmitri Sotnikov](https://pragprog.com/book/dswdcloj2/web-development-with-clojure-second-edition)
- [Clojure Applied From Practice to Practitioner by Bend Vandgrift and Alex Miller](https://pragprog.com/book/vmclojeco/clojure-applied)
