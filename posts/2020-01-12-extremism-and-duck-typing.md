---
layout: post
title: "Duck Typing and Talking About Extremism"
author: nfd
tags:
    - politics
    - criticism
    - "es: criticism"
    - "es: analogy"
    - "es: personal experience"
    - "cw: extremism/bigotry"
---

[In the wise words of James Whitcomb Riley](https://en.wikipedia.org/wiki/Duck_test):

> When I see a bird that walks like a duck and swims like a duck and quacks like a duck, I call that bird a duck.

#### Technical digression (just try to get the gist!)
We sometimes use this concept in software engineering.
We call it *duck typing.*
Say you have some object ``d`` in Python,
and you want to check if it's a duck at runtime.
How can we do this?
Well, we check if it can walk, quack, and swim.

```python
def isDuck(d):
    return hasattr(d, 'walk') and hasattr(d, 'swim') and hasattr(d, 'quack')
```
``hasattr(d, 'quack')`` is just digging into d to see if it contains some property 'quack',
and checking to see if doing so throws an exception 
(*very* loosely speaking, "throws an exception" means "tries to crash the program" here).
If it catches the exception 
(loosely "stops the program from crashing")
it answers "no",
otherwise it answers "yes."

Duck typing isn't used in all languages. Take, for instance, Haskell:

```haskell
ghci> class Duck a where walk :: a -> String; swim :: a -> String; quack :: a -> String
ghci> data Mallard = Mallard -- create a type (left-hand side) and a constructor (right) 
ghci> instance Duck Mallard where walk _ = "walked"; swim _ = "swam"; quack _ = "quack"
ghci> -- isADuck :: Duck d => d -> Bool
ghci> isADuck d = concat [walk d, swim d, quack d] `seq` True
ghci> d = Mallard -- construct a Mallard, and call it "d"
ghci> isADuck d
True
ghci> isADuck "some string"

<interactive>:51:1: error:
    • No instance for (Duck [Char]) arising from a use of ‘isADuck’
    • In the expression: isADuck "some string"
      In an equation for ‘it’: it = isADuck "some string"
ghci>
```
See that gross error at the bottom?
Haskell didn't actually let us get as far as checking if that string could quack.
Its type system is only willing to run ``isADuck`` if it already knows that what we're running is a duck,
i.e. it implements the Duck typeclass that we defined in the first line.
In order for a Haskell value to be considered to be a Duck,
I must assert to the compiler that it can do all the things that make it a Duck,
and that that makes it a Duck.
If I try to write code that calls a non-Duck a Duck, it won't even compile.

#### Okay, back to sanity

Alright, we've got our definitions out of the way.
Now, bearing in mind that *I know and admit that I'm reaching*,
 let's work towards the the part with the metaphor.

When people say things like "that bird is a duck"
or "that guy is a neo-nazi"
or "that tomato is a vegetable"
or "a poptart is a sandwich"
(the latter two of which I'll happily defend if pressured,
[@ me on the Fediverse](https://cybre.space/@nfd)),
they're trying to classify things in the natural world.
I'll call these things "natural objects."

Contrast people saying
"[a clopen set is a set that is both open and closed.](https://en.wikipedia.org/wiki/Clopen_set)"
Sets, including open and closed ones, aren't things that exist in the natural world.
You can describe the natural world using sets, but they aren't exactly natural objects.
Fittingly, pretty much everyone who has a reason to talk about clopen sets will not have any reason to be concerned that
the person they're talking to has a different conception of what "set" means,
simple-to-resolve confusion 
like "are we using [ZF or ZFC?](https://en.wikipedia.org/wiki/Zermelo%E2%80%93Fraenkel_set_theory)" aside.

You can't apply that reasoning to the question "Is a hotdog a sandwich?"

In fact, if you ask me that question, I'll argue that a hotdog is both sandwich and a taco.

Many of our natural-object classifications in everyday speech are fuzzy,
or they reflect our idiosyncracies. 
Philosophically, when we dig into them a little deeper,
they're all ultimately a bit fuzzy.

> What is a sandwich?

Well, it's something that lets you hold a foodstuff in some sort of starchy, non-messy, edible container.

> What's starch?

It's a bunch of glucose covalently bonded together.

> Okay, how much starch does it take to make something "starchy?"

Uhh, 50%?

> What's glucose?

C<sub>6</sub>H<sub>12</sub>O<sub>6</sub>.

> And what's a foodstuff?

You can see where this is going.

#### We're all using duck typing most of the time

It looks like a sandwich? Tastes like a sandwich? Call it a sandwich.
Sure, like, you might not think a poptart tastes like a sandwich, but that's not my problem.

I see this a lot in conversations about extremism.
Someone will say "person x is a Nazi" online today.
Others will take issue with this.
I'm usually not sure they know what the accuser is really trying to say.
In my experience, they're usually saying something to the effect of 
"when we're talking about some sorts of white nationalist extremists,
it's not worth trying our hardest to find all the distinctions we can between
them and neo-Nazis.
These ideas are poisonous enough that it would be wrong to treat the people who hold them with too much charity."
Responding with "no, the Nazis were members of the National Socialist German Worker's Party"
as a *denotational* counterargument is a category error.

If they're responding with a *connotational* argument,
whether or not I'd personally argue against them requires a bit more context.
If they're saying "no, the waiter who shortchanged you is not a Nazi,"
that's fine. If they're saying "Richard Spencer is not a Nazi,"
the most charitable response I'd be willing to drag up is
"I don't think you've put enough thought into the consequences of trying to defend Richard Spencer about this."

