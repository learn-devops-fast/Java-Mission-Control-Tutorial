---
layout: default
author: Cameron McKenzie
title: Start Java Flight Recorder example
blurb: Here's how to quickly kick off a Java Flight Recorder recording and profile your JVM's performance.
---

<div class="embed-responsive embed-responsive-16by9">
<iframe  src="https://www.youtube.com/embed/SzRq99Qy96Y" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

<img alt="eclipse jmc garbage collection" class="img-fluid" src="/assets/eclipse-jmc-garbage-collection.png">

# Starting Java Flight Recorder Example

hey I'm cameron mckenzie at cameron cnz
on twitter and
i want to talk to you about three ways
to start a Java Flight Recorder
recording
in eclipse so the easiest way to start a
Java Flight Recorder recording is to
just
run an application and then have java
mission control connect to it
so I've got a little do nothing program
here that does
nothing it's based on marcus hurt's lab
one exercise his online course it's very
excellent i
recommend you take a look at it anyways
I've started up this program here you
can see that it started if I go into the
debug window you can see that it started
right here

<img src="/assets/eclipse-jmc-perspective-button-toggle.png" class="img-fluid" alt="Eclipse Mission Control Perspective">

## Start Flight Recorder in Eclipse

Here I am in the jvm browser window
and
in this jvm browser window part of the
Java Mission Control
plug-in for eclipse that I've installed
you can see that it's got this list of
flight recorder recordings here and it
says hey there's no recordings but I can
say
start flight recording I can specify
the time I think only do it for 10
seconds I don't want to
sit here for a minute waiting for it to
be created you can
configure the name of the file I'll just
leave it as that file right there but
notice it's going to try and put into a
recordings folder
you can go in and set a variety of
configurations for the Java Flight
recorder I'm going to accept the
defaults
click finish you can actually see in the
bottom right hand corner it says this
is running and you can even see that
right there it says that it's
running too and once it's completed the
results will come up in Java Mission
control and then I've got the ability to
go through and
take a look at information about the
threads about the memory about
any information that is compelling
notice here it says that I've got a
number of competing resources running on
my computer
and that's the big feedback that is
getting giving me right now i
shut down as many background processes
if you want
dedicate more resources to your program
so that is option one
now you'll notice that on marcus hertz
program here he's got a bunch of
launchers and
one of the launchers is this do nothing
auto record
launch I'm gonna click on that and
you'll notice that in
this launcher he set some jvm arguments

<img src="/assets/eclipse-workspace-projects-loaded.png" class="img-fluid" alt="Java JMC JFR projects loaded">

## JVM Arguments to start Java Flight Control

and you can see if you go over here you
see it's
flight recorder arguments I'm going to
specify that
the recordings starts after one second
delay
has a 10 second duration and that the
file is going to be
saved to a in the o1 do nothing folder
and put the word auto at the end of that
file
and that's the file that will be created
for the recording so you can
set up your own launchers then when you
run the application you say
run as a java application
it asks you which launcher to use I'm
going to use the auto record launcher
click ok and you can see down here it's
saying hey we've started the recording
it's going to last for about 10 seconds
and when those 10 seconds are done
there should be a new file appear here
in this
do nothing project I may have to do a
refresh to see the file
and you can see it right there do
nothing auto dot jfr
I'll double click on that and now I can
see the automated analysis of
this application take a look at the
threads the memory
i think the same feedback comes here
that I've got too many
processes running by the way I'm going
to
just terminate those java applications
that are
currently running just so that I don't
have any confusion with
others that I might launch in just a
moment so I'm going to remove all of
those
terminated threads there and show you
the last way that you can
start a Java Flight Recorder recording

<img src="/assets/eclipse-jmc-launch-wizard-jfr.png" class="img-fluid" alt="Java Flight Recorder Launch Wizard">

### Java JCMD and Flight Recorder


simply
run an application so I'm going to run
this application I'll run this one down
here that doesn't have a launcher
associated with it just run
any java application it could be a
server it could be
tomcat anything running on a jvm you can
see that it's actually running there and
if I go to the debug tab
you'll see that it's running up here but
what I'm going to do I'm going to go to
the project
I'm going to right click in here and I'm
going to say
show in local terminal and so I'm going
to open up
the terminal window and from this
terminal window I'm going to just type
in jcmd
which is the java diagnose diagnostic
command tool and you can see it says
that
hey on that do nothing application is
running with a process id of 1836
and then what you can do is you do
something like this you can say hey i
want that java diagnostic command jcmd
to attach to 1836
that 1836 process is going to have the
Java Flight Recorder start
the Java Flight Recorder is duration is
going to be
i don't know equal to 10 seconds and the
file name
will be and I'll call this the jcmd
java javaflight java
flight recorder demo and then end it
with jfr
and if I've typed everything in
correctly there it will start the
recording it'll save it to
workspace my do nothing it's going to
take about 10 seconds for
that to be configured and run but I'll
do a refresh oh and forgive me I'm in
the wrong project i
might do nothing what do you what do you
say about a man with more than one watch
I've got to refresh the right project
and now when I've refreshed the correct
project you can see
that that java demo that java diagnostic
command
has now generated a Java Flight Recorder
recording for me as well
and so there you go those are three
separate ways that you can go about
generating a Java Flight Recorder
recording
in eclipse 

### Ways to start Java Flight Recorder

and there you go that's how
you start a Java Flight Recorder
recording
in eclipse now if you don't have that
Java Mission Control plug-in
installed check out the previous
tutorial because I show you how to build
it and
install it now if you want to learn more
about java Java Flight Recorder java
mission control or anything to do with
enterprise software development of the
java world head over to
theserverside.com I'm the
editor-in-chief over there we've got
lots of great tutorials and articles if
you're interested in my personal antics
you can follow me on twitter at
cameronmcnz
and subscribe on the youtube