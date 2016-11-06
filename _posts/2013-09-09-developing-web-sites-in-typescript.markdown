---
layout: post
title: Developing Web-Sites in Typescript
date: 2013-09-09 01:01:31.000000000 +02:00
---
![logo]({{ site.github.url }}/images/logo_small.png)

<p>I've started using typescript for my current project. It's a website that is very heavy on the client side with a lot of dynamic javascript code. While it's technically javascript, it's actually compiled typescript code. What does typescript offer, that you don't get immediately for free with javascript? A lot :-)</p>

<p>Typescripts offers well types :-), classes, interfaces and modules (i.e. namespaces). These are just the main selling points. It will also offer some more advanced features, such as simple mechanisms to deal with asynchronous I/O - borrowed from C#. Typing support is by far the most interesting feature, because it allows your IDE to check your reasoning at compile-time instead of letting you run into hard-to-debug errors at runtime.</p>

``` language-javascript
function radiansToDegrees(radians: number): number {
    return radians / Math.PI * 180;
}
```

<p>There are currently two main IDEs that offer very good Typescript support "Visual Studio 2012/2013" and JetBrain's "WebStorm". Although Visual Studio is developed by the same company as the language it doesn't offer a whole lot better support than WebStorm. WebStorm has their more reduced interface and less Windows-centric focus on their plus-side. When it comes down to price Webstorm can't be beat: <a href="http://www.jetbrains.com/webstorm/buy/index.jsp">44 euros + VAT</a> for a personal license, while Visual Studio clocks in at about 600 euros, but then Visual Studio is a full IDE for C++ and C#, too. Even JetBrains flagship product "Intellij IDEA" clocks in on only 180 euros for a personal license. Although I haven't done much with WebStorm yet, it seems very comprehensive and even features live-debugging with browsers other than the Internet Explorer. This might be a killer feature for me, because I like to become comfortable in my IDE and I don't like to use the browser's debugger, when I can avoid it.</p>

<p>Many people don't realize this, but every error you immediately fix when hacking in the IDE is worth a couple of minutes of debugging later on. That's also the reason typed languages are prefered for large projects.</p>

<p>Here's a <a href="http://channel9.msdn.com/Events/Build/2013/9-006">video</a> from the language creator Anders Hejlsberg, who also designed C# by picking the best from Java and C++. It seems Microsoft is doing better with typescript though, because they're keeping it open and openly support all platforms - what the heck, they even published it as open source. In his <a href="http://channel9.msdn.com/Events/Build/2013/9-006">talk</a> Hejlsberg lists typescripts advantages and talks about future extensions.</p>

``` language-javascript
interface IPoint {
    x: number;
    y: number;
}

class Point implements IPoint {
    constructor(public x: number, public y: number) { }

    public static add(point: Point, vector: Vector): Point {
        return new Point(point.x + vector.x, point.y + vector.y);
    }

    public reset(other: Point) {
        this.x = other.x;
        this.y = other.y;
    }    
}    
```

<p>In this slightly larger code sample, you see typescript's nice support for useful class constructs. You even get a taste for some nice syntactic sugar in Point's constructor that directly declares the member variables without listing them explicitly. As you can see this even works when they were declared as members in the interface. All this object-oriented goodness is not privy to some arcane plugin, that you have to install in your browser as would have been the case with Flash or Microsofts dead-on-arrival Silverlight. Instead it all compiles to clean readable javascript code. This is typescripts second big advantage over similar competitors like Google's <a href="https://code.google.com/p/dart/">Dart</a>. Both aim to support a more advanced javascript and both aim to be ubiquitous, but Dart's compiling to javascript is more of an afterthought.</p>

<p>Consequently typescript not only compiles to javascript but also has full compatibility to it, opening a treasure chest of millions of great libraries for developers that search both library support and type-safety. Volunteers have developed wrappers around many popular javascript frameworks that give you the type-safety when using them in typescript.</p>

<p>You can try out typescript directly on their <a href="http://www.typescriptlang.org/">website</a> or run the compiler from the commandline or as I prefer use it from an IDE like Visual Studio 2012 or JetBrains WebStorm.</p>
