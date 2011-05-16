---
layout: default
title: Laziness Sometimes Does Increase Productivity
published: true
categories:
  - information technology
tags:
  - linux
  - productivity
  - unix
---

To paraphrase what someone smart once said: Sometimes it's the lazy 
things in life that count.

Laziness does have it's rewards, as long as you are sure to pinpoint 
exactly what you want to be lazy about.  Case in point, long system 
operations.  Countless times I have transferred files, (un)compressed 
archives, or performed long operations and forgotten what I was doing 
while my terminal window was sitting in the background.  I have also 
had co-workers forget to hand me results because they were distracted 
by something else, and minutes or hours go by after the system 
operation has completed.

To solve this problem, you have to think like a lazy person, and how 
they would combat this situation.  Would a lazy person watch the 
terminal screen for minutes or hours until the operation finishes?  
Absolutely not.  They have more important things to do.  Instead, the 
lazy person would like to be notified when the processing has 
completed.  You could send an email, but mail routing can take minutes 
to complete (and your email client can be set to check mail once every 
10 minutes, defeating the purpose).  The next best thing to do is to 
alert yourself when the processing has finished with an audible alarm.

If you are running Unix or Linux, you can use the command *beep* to 
have the system send an audible beep whenever you call it.  You can 
alert yourself when the processing has finished by the following command:

    $ someLongOperation.sh; beep

If you are working on a system without the *beep* command, or you are 
not authorized to install it, you need to write your own script.  
Sending a control character to the *echo* command will produce the 
same results as above.  The script is as follows:

    ====beep.sh====
    echo -en "\007"
    ====beep.sh====

Now mark this script as user executable and run it.

    $ beep.sh

You should hear an audible beep from your computer.  Using this script 
to mark the end of a system operation is as follows:

    $ someLongOperation.sh; beep.sh

This will work so long as the beep.sh is in the current directory or 
somewhere on your *$PATH*.

Enjoy and be happy about using laziness to increase productivity.

