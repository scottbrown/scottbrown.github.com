---
layout: default
title: Books For A Budding Programmer
published: true
categories:
  - information technology
tags:
  - mentor
  - programming
---

In speaking with my mentee today, he asked whether I had any recommendations 
for real-world programming books.  I had to think about this question for a 
minute because of its apparent misdirection.

Typically, any real-world programming is done with a variety of languages, 
so I can’t just pick out the books that I have used to learn languages in 
the past.  These books have been obsoleted by newer versions of the language.  
But that is where the misdirection comes in; why should we look at 
programming languages when it is the art of programming that is more 
important in the professional world?  And so, I came up with this rather 
short list of my favourite books that teach a programmer how to be a better 
programmer.

[Mythical Man-Month][ref-1]
------------------

This book mainly focuses on how software projects are different from 
construction or other types of projects.  The content is taken from a 
real-world software project and helps the student to understand that 
professional programming has a lot more to do with communication and 
politics than it does about the act of typing code into a computer.

[The Pragmatic Programmer][ref-2]
------------------------

This book focuses any student programmer on the tools necessary to 
use in the workforce.  It may not be the exact tool being used by a 
company, but focusing on one tool allows you to understands its 
benefits and limitations.  Also, things that are rarely used in 
school, like version control, are discussed as necessary tools for 
any student.

[Refactoring: Improving the Design of Existing Code][ref-3]
--------------------------------------------------

This is a quintessential book for taking legacy code and modifying 
it to increase speed, reliability, readability, etc.  I have seen 
a lot of programmers who have not cut brand-new code for months on 
end, instead relying on legacy code fixes and upgrades to fill the 
void.  Working with legacy code typically sucks, because it was 
developed by someone else and, invariably, has little documentation 
or readability.  The maintainer has probably left a long time ago, 
leaving you with nothing more than the code to understand.  While 
working on legacy code, there may be better, faster ways to write 
the code or to decouple libraries from the core modules.  This will 
help in the future should a library need to be upgraded or replaced 
by another third-party.

[Clean Code][ref-4]
----------

In keeping with the previous theme, this book helps your descendants 
understand your soon-to-be legacy code.  Readability of code is key, 
and this book highlights real-world examples of inefficient, 
unmaintainable code.  Out of all the books on this list, this is one 
of the easiest books to devour, and even seasoned programmers should 
find this book a good refresher on good and bad habits.

[Patterns of Enterprise Architecture][ref-5]
-----------------------------------

I found this book to be useful when I started using interpreted 
languages like Python and Ruby.  Specifically, Ruby on Rails uses 
patterns from this book extensively.  For example, Rails uses an ORM 
called ActiveRecord, but I hate just taking someone’s word for it 
that it is going to work for me.  I found out that the ActiveRecord 
pattern is taken from this book, and I was able to understand the 
history and meaning of it.

[Design Patterns: Elements of Reusable Object-Oriented Software][ref-6]
--------------------------------------------------------------

More companies these days are using design patterns in their code.  
These patterns are simply best practices that have been vetted by 
some of the best programmers in the world.  After reading this book 
many years ago, I found it to help with understanding the common 
coding practices.  In professional programming, you are going to 
write the same type of code repeatedly, but for different projects, 
so these design patterns help to consolidate those repetitious code 
snippets into meaningful names.

[ref-1]: http://www.amazon.ca/Mythical-Man-Month-Software-Engineering-Anniversary/dp/0201835959/ref=sr_1_1?ie=UTF8&s=books&qid=1226696721&sr=8-1
[ref-2]: http://www.amazon.ca/Pragmatic-Programmer-Journeyman-Master/dp/020161622X/ref=pd_sim_b_2
[ref-3]: http://www.amazon.ca/Refactoring-Improving-Design-Existing-Code/dp/0201485672/ref=cm_lmf_tit_6_rsrsrs0
[ref-4]: http://www.amazon.ca/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/ref=sr_1_1?ie=UTF8&s=books&qid=1226697272&sr=1-1
[ref-5]: http://www.amazon.ca/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/ref=pd_sim_b_9
[ref-6]: http://www.amazon.ca/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612/ref=sr_1_1?ie=UTF8&s=books&qid=1226697249&sr=1-1

