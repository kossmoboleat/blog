---
layout: post
title: Trying out web development with Django
date: 2012-04-06 17:32:44.000000000 +02:00
---
I've wanted to develop for the web for quite some time. When I was younger I did some web design. But back then it meant that you probably had to learn ActionScript to get any kind of visually impressive design. Today most of it can be done with simple HTML, CSS and JavaScript. Fortunately there's also been a big trend towards simpler usable and clean web design approaches. Because all that seemed so interesting to me, I've begun to learn some bits in web development.

<div style="width:image width px; font-size:80%; text-align:center;"><img src="http://upload.wikimedia.org/wikipedia/en/0/0e/Spider_web.jpg" alt="Spider web taken or created by Fir0002" />Image taken or created by <a href="http://en.wikipedia.org/wiki/User:Fir0002">Fir0002</a></div><br/>Now that you can make pages look nice, you gotta start your journey to web design guru somewhere and instead of starting from scratch learning HTML5, CSS3 and JavaScript, I've taking the less steep road of using a ready-made web app framework. Python being my language of choice for learning new concepts it was only natural to start with its most popular web app framework Django -- after spending days researching this and deciding against "cooler" and less feature-rich alternatives like flask, bottle or cherrypy. 

One of the mantras of creating good software it to build something that you need yourself. It's not very deep but still true, as there's tons of abandonware of software projects programmers worked on but never bothered to finish or improve so they become generally usable. At my current company there's a group of people that alternate in cooking lunch for the group. Often the coordination who cooks lunch when and where is difficult and requires emails to everyone, that everyone has to respond to interrupting whatever you did before. It's no big surprise that <a href="http://www.pcmag.com/article2/0,2817,2354216,00.asp">email is broken</a>. A google search for "email is broken" yields 991.000 results and most of the time instant messaging is touted as its rightful heir. I don't like that solution very much because it interrupts you in an even more annoying way than email. My small web app tries to fix it by switching from pushing email to pulling the info from the publicly reachable web app.

<div style="width:image width px; font-size:80%; text-align:center;"><a href="{{ site.github.url | prepend:site.baseurl }}/images/lunch-organizer_version1_table.png" alt="" title="lunch-organizer table in version 1" width="637" height="403" class="alignnone size-full wp-image-490" /></a>table view</div>

<div style="width:image width px; font-size:80%; text-align:center;"><a href="{{ site.github.url | prepend:site.baseurl }}/images/lunch-organizer_version1_form.png" alt="" title="lunch-organizer_version1_form" width="177" height="157" class="alignnone size-full wp-image-492" /></a>edit date form</div>

I've made a small html table interface that is fed by an ORM that holds Lunch objects and can be edited using forms generated directly from the model. All this is surprisingly easy with django and the only hindrance for me was learning how to represent the control flow in a web app. I especially like Django's easy setup of the different ulrs that control the different functions of the website. This focus on urls also means that you have really nice clean urls instead of ugly <em>php?id=jfkdfjd</em>. Using regular expression you can match the parameters to the so-called "view function" and just use it as any old python method parameter

from urls.py:
<pre lang="python">
    (r'^lunch/$', lunch_template),
    (r'^lunch/new_lunch/(\d{4}-\d{2}-\d{2})/$', new_lunch_template),
    (r'^lunch/edit_lunch/(\d*)/$', edit_lunch_template)
</pre>

and from views.py:
<pre lang="python">
def edit_lunch_template(request,edit_pk):
    if  edit_pk == None:
        curr_lunch = Lunch()
    else:
[..]
def new_lunch_template(request,curr_date):
    if request.method == 'POST':
        form = LunchForm(request.POST)
        if form.is_valid():
            form.save()
            return HttpResponseRedirect('/lunch/')
</pre>

The code is all at github -- which is an awesome site and deserves a later post of its own. I've taken the opportunity to create my first open source this way ;-) :
<a href="https://github.com/kossmoboleat/lunch-organizer">github.com/kossmoboleat/lunch-organizer</a>
