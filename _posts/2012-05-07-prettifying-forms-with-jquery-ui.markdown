---
layout: post
title: Prettifying forms with jQuery UI
date: 2012-05-07 00:35:11.000000000 +02:00
---
I'm still adding little features and working on the design of my lunch organizer app. I've added nice javascript widgets for handling the input of dates and times. jQuery UI is a nice library that is the UI extension of the excellent jQuery library. Among many other things it features a very nice widget for <a href="http://jqueryui.com/demos/datepicker/">picking dates</a>:

<a href="/images/lunch-organizer_version7_form_datepicker.png" alt="" title="lunch-organizer_version7_form_datepicker" width="436" height="278" class="alignnone size-full wp-image-598" /></a>

Although the HTML5 <a href="http://www.w3schools.com/html5/html5_form_input_types.asp">input type "date"</a> hopefully brings us the functionality with simple HTML, we have to settle for this version for now (only Opera displays a special widget for the "date"-type). Unfortunately there's no default widget for time fields in jQuery UI. I'm not sure why that is so. Maybe it's selection process is a bit slow? I've looked at a number of widgets for choosing time and it's very refreshing to see how many interesting approaches have been invented for this:

<ul>
	<li><a href="http://fgelinas.com/code/timepicker/">François Gélinas' timepicker</a></li>
	<li><a href="http://haineault.com/media/jquery/ui-timepickr/page/#d-demo-wrapper-1">Maxime Haineault's inventive approach</a></li>
	<li><a href="http://labs.perifer.se/timedatepicker/">Anders Fajerson's simple time picker inspired by google calendar</a></li>
	<li><a href="http://keith-wood.name/timeEntry.html">Keith Wood's take, which reminded me of Qt's QTimeEdit</a></li>
</ul>

<a href="/images/lunch-organizer_version7_form_timepicker.png" alt="" title="lunch-organizer_version7_form_timepicker" width="346" height="258" class="alignnone size-full wp-image-599" /></a>

In the end I chose the excellent widget by <a href="http://fgelinas.com/">François Gélinas</a>.

When you download jQuery UI, you can pick and choose which functionality you need. There's a simple form, so you can minimize the size of the scripts each user has to download. The full package is over 1MB, thus this is really necessary. The simple selection with the datepicker and the position library is only 75KB (+25 KB for the images). The timepicker weighs in at an additional 60KB, which should still be tolerable.

The default size of the datepicker is much too big and it's not very obvious how you can reduce it. Fortunately the always helpful stackoverflow comes to the <a href="http://stackoverflow.com/questions/659588/how-to-resize-the-jquery-datepicker-control">rescue</a>. Add this simple style to your stylesheet and you will get nicely size date widgets:

<pre lang="javascript">
div.ui-datepicker {
    font-size: 75%;
}
</pre>

The same technique works for the timepicker:

<pre lang="javascript">
div.ui-timepicker {
    font-size: 75%;
}
</pre>

The next problem I had with these widgets were their default positions. Their default is just below the input field at its lower left corner. That way the datepicker covers the rest of the form and lowers the user experience. Of course there's a <a href="http://stackoverflow.com/a/1180538/731302">stackoverflow page</a> that helps with that, too:

<pre lang="javascript">
$("#id_date").datepicker({ 
    dateFormat: "yy-mm-dd", 
    beforeShow: function(input, inst) {
        inst.dpDiv.css({marginTop: - input.offsetHeight + 'px', marginLeft: input.offsetWidth + 2 + 'px'});
    } 
});
</pre>

For the timepicker there's not such an easy way, but it has two position attributes that let me achieve the same effect (at least in Chrome):

<pre lang="javascript">
    $("#id_time").timepicker({ 
    showPeriodLabels : false, 
    myPosition: 'right bottom', 
    atPosition: 'left bottom', 
    hours: { starts: 11, ends: 14 }
});
</pre>

When using the datepicker with Django, I had to make use Django's id format. It's always "id_<field-name>". Thus it was id_time for the field time. Of course I also had to add the stylesheets and the css elements to the head element:

<pre lang="html">
    &lt;link type=&quot;text/css&quot; href=&quot;/media/css/ui-lightness/jquery-ui-1.8.20.custom.css&quot; rel=&quot;stylesheet&quot; /&gt;	
    &lt;script type=&quot;text/javascript&quot; src=&quot;/media/js/jquery-1.7.2.min.js&quot;&gt;&lt;/script&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;/media/js/jquery-ui-1.8.20.custom.min.js&quot;&gt;&lt;/script&gt;
    &lt;link type=&quot;text/css&quot; href=&quot;/media/css/jquery.ui.timepicker.css&quot; rel=&quot;stylesheet&quot; /&gt;
    &lt;script type=&quot;text/javascript&quot; src=&quot;/media/js/jquery.ui.timepicker.js&quot;&gt;&lt;/script&gt;
</pre>

UPDATE: The new code is available at <a href="https://github.com/kossmoboleat/lunch-organizer">github</a>. I've also added the ability to delete entries and I am preparing to add permissions and user management soon.
