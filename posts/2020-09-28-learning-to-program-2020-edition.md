---
layout: post
title: "Learning To Program: 2020 Edition"
author: nfd
tags:
    - technical
    - advice
    - es: opinion
---
Here's my advice for how to learn to program, 
or how to up your programmer-game,
speaking as some kid with a computer science degree.
This is about how to become software-literate or a software-generalist.

*If I later decide to replace this post, 
this will be a link to the next step in the chain.*

### Beginners
Why do you want to learn to program?
Do you want to pick up some basic programming literacy to solve problems for yourself/for work,
or do you want to pick up software as a career or hobby?

### Beginners (Literacy path)
If you want to learn some basic programming literacy to solve problems for yourself,
go learn some Python.
I suggest just that you just do a web search for "learn python beginners,"
or look at the resources suggested on 
[the Python wiki's page for nonprogrammers,](https://wiki.python.org/moin/BeginnersGuide/NonProgrammers)
poke around to try to find a resource that looks like it'll work well for you 
(feel free to start a few and drop whatever you dislike),
and do the whole thing.

This will get you started out well enough that
you should be able to kind of bodge your way through other common,
simple programming tasks.
You'll be able to take the skills that you learned from learning Python and
apply them to tons of other technologies by
calling upon that experience to figure out what you'll need to Google to solve other problems.
(If you're a nonprogrammer,
you might think I'm trying to be insulting here.
I'm not.
This is actually how experienced developers solve a lot of their problems,
and [solving problems in lazy ways is a well-established feature of software folklore.](http://blogoscoped.com/archive/2005-08-24-n14.html))

### Beginners (Generalist path)
If you're a beginner and you really want to dig into how things work,
I suggest taking the Literacy advice above until you understand
variable usage,
basic control flow,
function calls,
string operations,
reading and writing to the console,
and reading and writing to files.
Then read and work through [K&R 2nd ed.](https://en.wikipedia.org/wiki/The_C_Programming_Language)
to learn C89.
Set up a Linux machine (or VM) and do your practice there.
Use whatever tools to do this that you want,
but start with [GCC](https://gcc.gnu.org/) plus [binutils](https://www.gnu.org/software/binutils/).
You can use a fancy IDE with visual debugging support if you like,
but make sure to learn [GDB](https://www.gnu.org/software/gdb/) at some point.
Decide on some programs you'd like to learn that feel like they're *just* past what you can comfortably write,
and work until you can write them.

If you need some ideas for tasks, here's a few, roughly in ascending order of difficulty:

- CLI calculator
- a small game (maybe one JRPG-style combat?)
- an interactive love letter for someone
- solve some LeetCode/HackerRank/Project Euler/Advent Of Code/... problems
- your own text editor
- your own simple Unix shell
- your own simplified version of `make`
- socket-based two-way chat program
- socket-based many-clients one-server chat program (maybe [IRC](https://tools.ietf.org/html/rfc1459) if you're feeling brave!)

(The programs you write should be pretty basic for a pretty decent amount of time!
That's normal!)

Make sure to learn about...

- pointers
- arrays
- structs
- stack memory vs. heap memory
- bitwise operations
- unsigned vs. signed integer types
- basic assembly for your platform (and ideally for x86/x86_64 if you haven't), or at least enough that you can follow along with a debugger or figure out the meaning of a loop when you eyeball it
    - ...which also entails learning the basics of the registers for your system, what it means to load things from memory, and why some small variables never turn into memory loads
    - ...and the basics of the memory/cache hierarchy, *and the implications this has on the performance impact making your loads sequential*
- what C strings are, and why they aren't acceptable for representing text in modern applications
- IEEE 754 floating point
- C's "type system," why it's just a suggestion, and the meaning of the conventional use of `void *`
- file descriptors and FILEs
- sockets
- blocking/nonblocking IO, use of `poll` 
- signals/`kill`, signal masking, signal handling
- fork and exec
- the basic role of pid 1 (only the parts that exist in [sinit](https://git.suckless.org/sinit/file/sinit.c.html), since systemd is NOT basic, for better or for worse)
- pthreads (I highly recommend [this book](http://greenteapress.com/semaphores/LittleBookOfSemaphores.pdf) as a supplement)
   - Solve a problem where multiple threads don't need to share memory, and solve another problem where they do.
   - Sketch out solutions for the [dining philosophers problem](https://en.wikipedia.org/wiki/Dining_philosophers_problem), the [cigarette smokers problem](https://en.wikipedia.org/wiki/Cigarette_smokers_problem), the [producer-consumer problem](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem), the [bounded-buffer problem](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem), and the [sleeping barber problem](https://en.wikipedia.org/wiki/Producer%E2%80%93consumer_problem).

You might read all of that and think
"whoa, nfd's really throwing me in the deep end. What's up?"

I am.
That's the point:
to really begin to dig into this sort of stuff,
you need to get comfortable figuring things out as you go,
trying different tools,
and figuring out what sorts of resources will help you to
overcome the kinds of hurdles that you come across.

Remember that you're learning to solve practical problems in practical ways:
it's never "cheating" to Google something you're unsure about, or to use `man`.
It's also *completely fair* to pick up other programming skills concurrently with all of this,
including the skills that I'll list later in the guide,
if you find the need or desire to do so.
What I just described is something close to a minimal viable set of knowledge/skills that you'll need to become a systems developer.
Knowing what you're doing at the systems-level will help and inform your problem-solving abilities in a lot of
non-systems work.

...and if you got through that, congrats.
You've basically covered the content of the four most important courses I took in my computer science education,
plus a little.

### Intermediate/Advanced

- ***Write some programs and libraries.***
- Learn shell scripting on at least your preferred platform and on POSIX systems.
- Learn Java and/or C#.
- Skim [Gang Of Four.](https://en.wikipedia.org/wiki/Design_Patterns)
- Learn a Lisp (Racket's always a good choice).
- Learn SQL, learn relational algebra, learn basic optimization skills.
- Learn a modern low-level {} language like Rust.
- Learn a modern OO language like Kotlin or Scala.
- Write a program for some old-school hardware in 6502 asm, Z80 asm, or similar.
   - If you want people to be able to run your program forever, write it for the Nintendo Entertainment System.
- Learn some other weird languages if you want. I like Haskell, for example.

