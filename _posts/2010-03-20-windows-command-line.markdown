---
layout: post
title: Windows command-line
date: 2010-03-20 18:03:52.000000000 +01:00
---
The thing I always miss most on Windows is the command line -- well and Spotlight, but that's for another post. And if you look at the cmd.exe, its just extremely badly done. It's a fixed font, fixed width window with way too small font. I don't want to go too  much into detail, but it's very lacking. Even the newest and greatest Windows has this bad terminal emulator/shell. 

But oh brother, there's salvation! The mighty god of open-source software development has blessed us with two great pieces of software: "Console2" and"bash". "Console2" offers what any other old terminal emulator already has,holy!, even xterm is better than cmd.exe! Sure you might mention that there's at least Powershell (Can you think of a cheesier name?), but then you're still stuck with the terminal emulator cmd. Ok, so Console2 has configurable windows size, variable font, coloring and tabs. And the greatest thing for me is that I can even select text with this extremely modern device called a mouse! I always get so exited when I have the chance copy something by selecting and pasting with the middle mouse button. 

And then there's this other little thingy called bash. Using cygwin you can actually get a hold of this extremely powerful UNIX shell. There's a whole lot of examples how to write in its little language in comparison to the embarrassed giggles that you receive when you ask somebody if they knew how to use the "Powershell". Ok, so bash is what you want as a shell, seriously. It's standard on the mac and virtually all Linux distributions. It also has tab completion how god intended it, because it does not just stumble through all the files in a directory but lists all possible completions if there is no unique one.

Ok, to make this hopeless rant helpful for you here are some tips to get a nice terminal in Windows:

- Install <a href="http://sourceforge.net/projects/console/">Console2</a> and <a href="http://www.cygwin.com/">Cygwin</a>
- Setup an entry in your explorer context menu to start a shell where ever you want (the inverse direction is even simpler: "explorer.exe ./"
- Familiarize yourself with the command "cygwinstart" (it's the equivalent of Mac's open command): it automagically opens the correct application for a specific file extension
- If you're using Eclipse get the <a href="http://marketplace.eclipse.org/content/easyshell">EasyShell</a>(<a href="http://pluginbox.sourceforge.net">update site</a>) plugin and setup to start a Console2 bash; After this <a href="http://www.ghisler.ch/board/viewtopic.php?t=25193">thread</a>, I found a way to specify it: 
<ol>
<li> add the cygwin/bin directory to your PATH variable</li>
<li>in your bash startup files (/etc/profile, /etc/bashrc, $HOME/.bashrc, $HOME/.bash_profile) remove any commands that change the directory on startup, suchs as cd $HOME and so on</li>
<li> in Console define your bash tab configuration to start bash --login -i</li>
<li>start console2 with a command "<path_to_console>/Console.exe -t "<your_bash_tab_cfg>" -d "<startup_dir>" (in easyshell this should be {1})</li>
