---
layout: post
title: "Some Notes on Hostile Community Formation"
author: nfd
tags:
    - essay
    - short
    - technical
    - "es: criticism"
    - "cw: extremism"
---
Some thoughts on hostile forks/hostile offshoots, discussion of Suckless.

There's a concept in the free software world of "hostile fork:"
a fork that's motivated by some sort of perceived shortfalling
in a project's direction or leaders.
Sometimes it's personal, 
sometimes it's a result of internal disagreements about an organization's finances,
sometimes it's because a Benevolent Dictator is being a bit too dictatorial for
the forkers' preference.

Suckless has a strange internal culture that I'd have a hard time summarizing.
[Here's some cat-v insider's personal summary,](https://harmful.neocities.org/)
[here's their 2017 conference/hackathon photos,](https://suckless.org/conferences/2017/)
[and here's discussion of one of their insiders acting--well--pretty fashy.](https://twitter.com/pid_eins/status/1113738766471057408)
If you were to ask *me,*
I'd say the range of reasonable reactions to the org range between
"they're elitist in a really backwards way"
and "they're [a little bit too hard to distinguish from neo-Nazis
for me to really want to look into this too hard.](/2020/01/12/extremism-and-duck-typing/)"

They've written a bunch of software that's, well, mostly fine in itself?
Like, you're probably going to be really surprised by the exact ways it's barebones
(ever tried to get Unicode working well in st?),
but most of it solves some basic problem in some basic way and does so passably portably.
Extensions and customizations are applied as patches to the project's sources, in C.
Some well-known and decent projects like [awesome](https://awesomewm.org/) and [xmonad](https://xmonad.org/) are
extended semiclones of Suckless' dwm.
(I personally first used dwm back in college,
when I desperately wanted to get xmonad working on the university workstations,
but couldn't quite get it working due to the systems missing some development headers and etc.
dwm, built on my laptop with a couple patches, worked fine!)
I assume pretty much everyone who would rather be using xmonad or i3 or Sway
than some patched dwm already are,
and it's not the kind of tool that people are going to start using by accident if they didn't like it.
GNOME and MATE and KDE and xfce already fit the more-normal approach to desktop environments pretty well,
and "more-normal" is a perfectly good thing to be.

If you ask me, there's nothing uniquely wrong with the code itself,
and there are occasionally decent reasons to use really simple/portable/basic code
when you're trying to get simple viable systems running.
Could, for instance, dwm and its tooling be a decent situation for a hostile fork?
TL;DR? Eh. Maybe it needs a hostile *cultural* fork.

dwm's code isn't uniquely good, and it's not uniquely well-maintained,
and it'd probably be plenty easy to fit those same basic requirements I was talking about
(i.e. the basic consequences of its particular minimalism,
not Suckless's dogmatic obsession with that minimalism).
You could pick a more-modern language that's easy to rig up with LLVM's toolchain,
you could build some proper extension scaffolding,
you could build some configuration system for those extensions to use,
and you could encourage continuing development on the project's functional core
to deal with localization/security/stability issues instead of Suckless's
we-don't-have-to-maintain-localization-and-compatibility-code-if-we-never-bothered-to-do-anything-about-that-stuff-in-the-first-place approach.
There's no deeply-entrenched technical core of dwm to need to overcome.
I think this means a new project (or five!) would be fine.

That basic idea of supplying minimal, simple, portable code for people who need it
or might want to bootstrap something bigger with it?
Great. Perfect. That sort of thing needs to exist, even if it's not for everyone.
Maybe we need to "hostile fork" this aesthetic of minimalism
to permit it to be more approachable, more welcoming, and less elitist.
Elitism and exclusion aren't "simple."
I try to embody that ideal when I interact with people in IM chatrooms/IRC/etc.
looking for support when they're learning new tools, whether they're "minimal" or not.
