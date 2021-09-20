---
layout: post
title: "foldl' (flip ($))"
author: nfd
tags:
    - technical
    - tiny
---
Just a quick Haskell pattern for you.

```hs
foldl' (flip ($)) :: Foldable t => a -> t (a -> a) -> a
```
It's a handy gadget if you ever need to quickly compose a bunch of
endomorphisms (sorry, values of type `a -> a`) and thread a value through them.
This may smell like the 
[Endo newtype](https://hackage.haskell.org/package/base-4.8.2.0/docs/Data-Monoid.html#t:Endo),
given the sweet monoid perfume you may have noticed.

Arguably a bit more legibly/conveniently, there's this thing:
```hs
foldr (.) id :: Foldable t => t (b -> b) -> b -> b
```

You may find use for this with other functions like `foldM`.
If anybody has an idea for a good name for these, I'm all ears.
I'm sure people have been using this for a good long while, after all...

