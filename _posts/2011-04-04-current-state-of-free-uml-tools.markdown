---
layout: post
title: Current state of free UML-tools
date: 2011-04-04 23:51:51.000000000 +02:00
---
I recently changed jobs from working on a project with code-generation and modeling component to a job without this. In my old job I  have learned to value the importance of modeling future designs and documenting your architecture using UML-models. We had the good fortune than to need a specific commercial editor called MagicDraw for our code generation framework based on Eclipse. Although rather too complicated in the beginning it had become a very useful tool for me.

Now at my new job I started with getting to know the codebase and creating some documentation along the way. As we don't have a requirement for code generation. there are no licenses available for any commercial UML editor and I began searching for a freely available commercially usable alternative. To cut a long story short; all the solutions lack either in functionality or ease-of-use.

My requirements for an UML-tool for documentation are very simple:
<ul>
<li>class diagrams which support generalization, association and aggregation with multiplicities and names</li>
<li>sequence diagrams that support reflexive messages, normal messages and returns with names</li>
<li>drawing functions that stick to objects and let me click to edit names and multiplicities</li>
<li>some automatic logic for sequence diagrams that creates horizontal lines for the messages</li>	
<li>some automatic layout functions that let me drag and reorder objects and <strong>leaves</strong> everything else intact</li>
<li>modern-looking graphics (UML diagrams are already dry, the graphics don't have to overemphasize that though)</li>
</ul>

The most often cited tools are <a href="http://argouml.tigris.org/">argoUML</a>, <a href="http://staruml.sourceforge.net/">StarUML</a>, <a href="http://bouml.free.fr/">BOUML</a>, <a href="http://www.horstmann.com/violet/">violet</a> and <a href="http://www.umlet.com/">umlet</a>. Except violet they all have the required functionality. Violet is just too basic for what I need. The problem is the ease-of-use because they either have too many dialogs when editing or they won't let you edit text easily or rearrange the elements for a different layout. I found an unlikely half-decent alternative in the UML component of the Java-IDE <a href="http://www.oracle.com/technetwork/developer-tools/jdev/downloads/index.html">JDeveloper</a> (get the studio edition). It supports the automatic layout functions I want somewhat but beware of some moves which make it move all the labels away from their respective lines. This is a real PITA and I'm still on the lookout for some good modern-looking contender. One possible tools for class diagrams could be <a href="http://yuml.me">yuml.me</a>, which is a web app that uses a straightforward syntax to allow you to describe associations with all the details. I'm going to try it soon, but I still need sth. for sequence diagrams.


