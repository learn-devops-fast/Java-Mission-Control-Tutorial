---
layout: default
author: Cameron McKenzie
title: How bad Java code leads to performance problems: JDK Mission Control
blurb: Here's how to use Java Flight Recorder & Mission Control to identify bug ridden code that causes a JVM performance problem.
---

<div class="embed-responsive embed-responsive-16by9">
<iframe width="560" height="315" src="https://www.youtube.com/embed/XK0WSi-cpVw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
</div>

# Java Performance Troubleshooting
hey i'm cameron mckenzie [@cameronmcnz](http://www.twitter.com/cameronmcnz)
on twitter and i wanted to talk to you
about
java auto boxing and the performance
implications that
boxing and unboxing your java primitive
types can have
on your jvm to demonstrate the
performance implications of boxing
and unboxing java primitive types i've
got this example which is based
loosely on one of the examples in marcus
hertz jmc tutorial i highly recommend it
what i've got is i've got a class here
called snoop int which is really just a
wrapper class for
an int field it's got one int and a
getter for it
named it after snoop dogg because he's a
rapper as well
and then i've got this other class that
does some java primitive type
auto boxing and i've named it after a
great boxer mike tyson
and as you can see here we declare a map
a collection class and we put 700
000 elements in it we're testing
performance for sure
and each of these elements is just one
of those snoop objects the
number from 0 to 700 000 goes in as the
id and then we use the same field as the
key for the java map okay so we end up
getting a java map with 700 000 elements
in it and then we do this very contrived
example where we take a copy of all the
values
and with the copy of all the values we
then check to see
if each individual copy can
is has its corresponding id
in the original map so i mean we're
basically unit
testing that um the map.values method
works but it
causes a bunch of objects to be created
and comparisons to happen

## Java Performance Problem Example


it's a good little test just to see
how
boxing impacts performance so i'm going
to run this application so here's
my mike tyson class i'll say run as a
java application
i'm going to use my auto record java
flight recorder
launcher i can show you that in just a
moment if i come over well i guess i
can't show you that because
um this is gonna keep running so much
there it is i'll open up this launcher
and i've got an auto launch here which
says hey when this particular
application runs
kick off java flight recorder
delay a few seconds as you start and
record for 120 seconds now
i think i've probably got enough
recording right here so
i'm going to click enter that's going to
cause a
new file to be created that's my java
flight recorder file
and i'm going to open up that java
flight recorder recording
with the java mission control eclipse
plugin it's going to think about that
file for just a second and when it comes
up you'll see it's flagging allocated
classes if i ran this a little bit
longer this would have come up red
right now it's just a yellow warning but
it's saying hey you've got a problem
the most allocated type is integer here
we've got it
using value of it's in this run class of
mike tyson
and this is a pretty good place to start
identifying
your performance problems 


<img alt="JMC JMX Mbeans management console" class="img-fluid" src="https://itknowledgeexchange.techtarget.com/coffee-talk/files/2020/12/java-autoboxing-performance.jpg"/>

### Troubleshooting with Java Mission Control


if i go over
to
jvm internals and look at garbage
collection
this is where you really start to see
some of the issues so i think i might
get rid of the
heap post gc there and get rid of the
metaspace used and you can see this
garbage collection is going
up and down like crazy here and you can
see that
there's pretty long pauses so i've got a
pause here
of 889 microseconds i get a pause here
of 700. so i mean these
are significant pauses they've got 1.316
so as the program
runs the garbage collection takes longer
and longer to do
and this will really start to consume
large amounts of memory as well
and if i actually take a look at some of
the memory over here looks like whoa
java.lang integer six point no wonder i
was getting
out of memory exceptions the last time i
tried to run this with eight threads
yeah that's a huge amount of memory
that's getting consumed here
okay so here's the fix i'm gonna go into
my code hey marcus
i'm gonna go into my code i'm gonna go
into this
snoop in class and where it's just int
i'm gonna just replace it with integer
okay quick change three changes there
and now
i have to actually make this change over
here so instead of
i it's integer dot value of
i and do the same thing over here so
that now when i'm putting the objects
into the collection class i'm not doing
java primitive type auto boxing i'm
doing that boxing myself now but now
i've got reference types in the map the
object is a reference type i don't need
to do any java primitive type
boxing or unboxing all of the the
actions are done with me i use the
wrapper class in
every instance i'm going to go over to
my launcher just take a quick look at
that launcher there
that's not the launcher that's the
flight recording here's the launcher i
was going to rename change the name of
the file that i create so i'm going to
call that
allocation 2 click save
and i'll run this again and hopefully i
won't get any out of memory errors in
fact i think this will run
much more efficiently.

### Java Flight Recorder and Performance Profiling



 so i'll click run
as java application
say hey do that java flight recorder
recording so i can look at the results
of the
profiling in java mission control it's
going to run for a few seconds here
i'm going to go over to package explorer
i got that console issue again
there we go put the console over there
i'm gonna do a little refresh here on
recordings and i should see
a new file created okay now we're still
writing to that file
i think i'll come down here and
terminate this application
and now open up the second allocation
file the second running
of the jvm flight recorder and you can
see here
the warnings about the garbage
collection and the auto boxing
of java primitive types the performance
problems that
were indicated earlier are gone and if i
come over here to
garbage collection you can actually see
i don't even have any metrics on garbage
collection like i don't think garbage
collection even
happened that whole time and if i look
at memory.


<img alt="JMC JMX Mbeans management console" class="img-fluid" src="https://itknowledgeexchange.techtarget.com/coffee-talk/files/2020/12/java-mission-control-gc-garbage-collection.jpg"/>

i had gigs before and now i mean
i like it that's like the size of uh
smaller than a youtube video size of a
big graphic on a website
um and all of that was achieved simply
by
avoiding the use of the autoboxing of
primitive types in the application
i just use the integer class in each
instance
we don't have to switch from primitive
type to wrapper class wrapper class to
primitive type
we just use the reference type
everywhere and the auto boxing of java
primitive type performance problem goes
away
now i have to say this really surprised
me and i should probably say thanks for
marcus for pointing this out to me but i
thought that when they introduced
auto boxing in jdk 1.5
that part of that was performance
improvements
to make sure that the auto boxing
process didn't
have serious performance implications
like causing
seven gigs of memory to be allocated as
you go through a map
i was clearly wrong and you know it's
one thing to have an assumption
but if you do have an assumption make
sure there's some way to validate that
assumption
otherwise you can find yourself in
serious performance problems now that's
one of the great things about
java flight recorder and the java
mission control
you can go in here do recordings and
validate those assumptions
and avoid introducing serious
performance
problems in your applications and there
you go there's some
interesting insights from java mission
control and java flight recorder on
java auto boxing of primitive types now
if you enjoyed that tutorial
head over to theserverside.com i'm the
editor chief over there we've got lots
of great tutorials on
java jakarta ee devops enterprise
software you name it
if you're interested in my personal
antics you can always follow me on
twitter
