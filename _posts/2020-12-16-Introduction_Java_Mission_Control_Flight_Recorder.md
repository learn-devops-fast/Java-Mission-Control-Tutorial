---
layout: default
author: Cameron McKenzie
title: Introduction to Java's JDK Mission Control
blurb: Here's a very quick introduction to Java Mission Control and the JVM Flight Recorder.
---

<div class="embed-responsive embed-responsive-16by9">
<iframe  src="https://www.youtube.com/embed/AHT4ZvOe6a4" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<img alt="eclipse jmc garbage collection" class="img-fluid" src="https://itknowledgeexchange.techtarget.com/coffee-talk/files/2020/12/Java-Mission-Control-Eclipse-Plugin-JFR.jpg">

<img src="/assets/eclipse-jmc-launch-wizard-jfr.png" class="img-fluid" alt="Java Flight Recorder Launch Wizard">

# Introduction to Java Mission Control

hey i'm cameron mackenzie at cameron
mcnz on twitter and i wanted to talk to
you about java mission control and
specifically give you a quick overview
of java mission control show you how to
very quickly
download it and install it get it up and
running show you how to actually
connect to an existing java virtual
machine and then
do a java flight recorder and take a
look at some of the memory used and some
of the cpu usage and all the interesting
things that
make your java virtual machine tick to
work with java mission control 

<img src="/assets/eclipse-jmc-launch-wizard-jfr.png" class="img-fluid" alt="Java Flight Recorder Launch Wizard">

## Download JDK Mission Control

you have
to
download it it doesn't come packaged
with the jdk anymore there's a few
different versions the
azul version is a fantastic option you
can get a version from
oracle there's also the adopt open jdk
version which i like so i'm just going
to click on this
download button it downloads a 65 meg
file into my downloads folder you can
see it right there now i actually like
to
put all of my important tools in a
folder called tools so i'm going to
paste that zip file
over there and then just do a 7-zip
extract to
appropriate folder it creates the
java mission control folder right there
i'm just going to give it a bit of a
rename
java mission control and inside this
folder there's an
executable file which i'm going to click
on that's a java
mission control right there as you can
see jdk mission control
7.1 comes up takes just a minute to load
and as it loads it's going to find all
of the jvms that are running on my local
system one of which is actually going to
be this
jetty server here and as you can see
i've actually got
jetty running on localhost 8080. 

## Profile Jetty with Mission Control

so
mission control comes up
you get a bit of a nag screen here it
says hey there's a bunch of tutorials
out there
and those tutorials are great but this
tutorial is great as well so i'm going
to close that
nag screen and you can see it's actually
identified a couple of jvms that exist
the jvm browsings tab
the jvm browser view shows you different
jvms that have already been discovered
there's options in here like to start
the flight recorder you don't have
anything interesting to look at until
you've done a recording well
maybe i shouldn't say that you can't
always look at the mbean server the
ambient server just gives you some
feedback
on how your jvm is running right now so
i've got
as i said a jetty server there you can
see jetty colon run was the maven
command that triggered that to go up and
it looks like there's not too much going
on there i can see those dials but let's
see what happens if i do a couple of
refreshes
on my site here to try and see oh there
we go we actually can see those
needles moving a little bit the memories
being used i'm going to click the back
button
trigger some refreshes on that site as
well
and uh yeah you can actually kind of see
that needle move a little bit so that's
kind of cool from that mbean server yeah
i see a little bit of movement there and
increase in memory
as i try and do some operations but
we're here to talk about
java mission control and java flight
recorder and so let's talk about
doing a java flight recorder recording
how do you do it well
you simply click on flight recorder over
here say start
flight recording and all of a sudden a
process will go off that will
gather information from the jvm that
you've got singled out i'm going to
specify to go for a minute i'll call it
my recording

### Java Flight Recorder and Mission Control


i'll click finish and now the
java flight recorder is going to go take
a bunch of information about this jvm
hosting
jetty and so i guess it is a good time
to maybe go back
and do a bunch of refreshes on that
server there
and put it under some sort of a load we
can see the number of megs being used is
increasing and
looks like maybe even some of the jvm
cpu usage is going up and
down a little bit as well so just a
couple of interesting
things that happen i can see a couple of
spikes you can see
all of a sudden the memory is going up
we're about 58
60 percent through our one minute
recording now again this is the
m-bean server this is giving us some
live feedback on
how our jvm is behaving um this isn't
the mission control report though we're
going to get that
once that flight recorder has finished
recording.


### View Recordings in Java Mission Control


and there you go this is the result of
that flight recording uh it's
right off the bat it's not giving me too
much information other than saying hey
you've got a whole lot of processes
running on your computer and this jvm is
competing with
40 other processes but over on the left
hand side here you can see i can get
some more detail like i can get
some information about the memory and
how it was used
you can see over here during that one
minute look like memory spiked a little
bit and that was probably as i was doing
all of those
refreshes you get informations on
threads that were running threads that
were blocked threads that were stopped
information about garbage collection
that may have happened
any processes that were running
all sorts of information about just what
happened during that run as i said you
can see even a little bit of cpu
peaking here cpu usage peaked as i did
the refreshes
after about 30 seconds i stopped doing
those refreshes so it really kind of
balanced off and you can actually kind
of see that in the recording
and yeah so that gives you just an
overview of how
this java mission control works and how
the
gui looks as well you've got the
properties tab to the lower left
gives you more information on any of the
fields that you have
clicked on over on the left hand side
you've got
results that have occurred through the
recording and information about some of
the stack traces that have happened as
well

<img alt="eclipse jmc garbage collection" class="img-fluid" src="https://itknowledgeexchange.techtarget.com/coffee-talk/files/2020/12/Java-Mission-Control-Eclipse-Plugin-JFR.jpg">

### Java Mission Control Overview

you've got the opportunity to kind
of choose different fields that you want
to grab
information about and there you see that
stack trace coming up when i
click on asking for information about
the used heap
and there you go so that's just a very
quick and
basic overview of the java mission
control
standalone application for the rest of
the
tutorials that i'm going to do i'm
likely going to do the
java mission control and java flight
recorder examples
using the eclipse plugin that puts java
mission control
right inside of eclipse right next to
your code and there you go that's a
quick overview of the java mission
control now i've got a
number of subsequent tutorials that are
going to go a lot more in depth but that
gives you a quick introduction on
how to install it how to use it and some
of the cool information that can give
you about your jvm now
if you enjoyed this tutorial head over
to theserverside.com i'm the
editor-in-chief over there
we've got lots of great tutorials on
java java mission
control enterprise software development
devops you name it
if you're interested in my personal
antics you can always follow me on
twitter
at cameronmcnz and subscribe
on the youtube