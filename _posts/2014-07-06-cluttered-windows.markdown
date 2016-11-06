---
layout: post
title: Cluttered Windows
date: 2014-07-06 17:50:14.000000000 +02:00
---
If you're desk is cluttered it's hard to concentrate. The sight of large headlines of your favourite magazine or some unpaid bill is a sure way to direct your thoughts from the task at hand. Even so most of us fail to organize their digital work in the same way. Take for instance application windows.

<a href="https://www.flickr.com/photos/carsten_tb/7173481425" title="Window compositions by Carsten ten Brink, on Flickr"><img src="https://farm8.staticflickr.com/7075/7173481425_1b2f005806_c.jpg" width="800" height="534" alt="Window compositions"></a>

If you do any kind of digital work, you probably need at least a browser and your word processor/editor/photoshop or similar open. Sometimes you have to look up something and you keep switching between the two. If you don't have two displays -- [which you probably should](http://blog.codinghorror.com/does-more-than-one-monitor-improve-productivity/) -- you lose your context every time you switch and have a much lower productivity as a result.

One of the most popular solutions to this is Windows' "sticky sides". Move the window to the side of the display and it takes up the whole half of the screen. Moreover you can press **windows_key + left/right** to move a window to the left or right half. With Mac OS X you can do similar stuff with a number of programs: 

- [Flexiglass (9 Euro)](http://www.nulana.com/flexiglass/)
- [SizeUp (13 Dollas)](http://www.irradiatedsoftware.com/sizeup/)
- [Slate (open source, development discontinued)](https://github.com/jigish/slate)
- [Divvy (14 Dollars)](http://mizage.com/divvy/) 
- [ShiftIt (open source)](https://github.com/fikovnik/ShiftIt)

Not only can you divide your screen real estate by 2, you can also organize by 4 or sometimes even devise your own separations, e.g. 1/3 to 2/3. For Windows there are also more powerful tools, i.e. [GridMove](http://jgpaiva.dcmembers.com/gridmove.html).

Of the above lot [Slate](https://github.com/jigish/slate) is my favorite, because it's free, combines the power of the others and can be extended for even more use cases (starting a selection of programs in a specific configuration for example). Unfortunately it's development has been discontinued for some time, but it still works very reliably and serves its purpose. This is my current config (I mapped the caps-lock key to cmd+option+alt+ctrl before using the excellent [KeyRemap4MacBook](https://pqrs.org/macosx/keyremap4macbook/) and [Seil](https://pqrs.org/macosx/keyremap4macbook/seil.html.en)):

{% highlight shell %}
# Abstract positions
alias full move screenOriginX;screenOriginY screenSizeX;screenSizeY
alias lefthalf move screenOriginX;screenOriginY screenSizeX/2;screenSizeY
alias righthalf move screenOriginX+screenSizeX/2;screenOriginY screenSizeX/2;screenSizeY
alias topleft corner top-left resize:screenSizeX/2;screenSizeY/2
alias topright corner top-right resize:screenSizeX/2;screenSizeY/2
alias bottomleft corner bottom-left resize:screenSizeX/2;screenSizeY/2
alias bottomright corner bottom-right resize:screenSizeX/2;screenSizeY/2

config defaultToCurrentScreen true
# Shows app icons and background apps, spreads icons in the same place.
config windowHintsShowIcons true
config windowHintsIgnoreHiddenWindows false
config windowHintsSpread true

# Numpad location Bindings
bind pad1:shift,alt,cmd,ctrl ${bottomleft}
bind pad2:shift,alt,cmd,ctrl push bottom bar-resize:screenSizeY/2
bind pad3:shift,alt,cmd,ctrl ${bottomright}
bind pad4:shift,alt,cmd,ctrl ${lefthalf}
bind pad5:shift,alt,cmd,ctrl ${full}
bind pad6:shift,alt,cmd,ctrl ${righthalf}
bind pad7:shift,alt,cmd,ctrl ${topleft}
bind pad8:shift,alt,cmd,ctrl push top bar-resize:screenSizeY/2
bind pad9:shift,alt,cmd,ctrl ${topright}
{% endhighlight %}

A new project called [hydra](https://github.com/sdegutis/hydra) with even higher aspirations -- can you say feature-creep? -- appeared recently to take up the legacy. I hope that the developer will not lose his momentum, because it looks very useful right now and I'll have to dig in and test it out very soon...
