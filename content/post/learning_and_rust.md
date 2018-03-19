+++
Categories = ["Development", "Rust"]
Description = ""
Tags = ["Development", "rust"]
date = "2015-12-29T12:32:33-05:00"
menu = ""
title = "Learning and Rust"

+++

Rambling thoughts ahead:

So, it looks like after pushing for Haskell, it didn't work out (yet, at least). I think that it's partly because my mindset is not currently capable of keeping up with Haskell's abstraction levels, and also that Haskell is difficult to move from toy to "real program", at least in my experience.

In any case, in the fall, I decided to focus less on Haskell. The stuff I cared most about was functions like map, filter, and fold, as well as structuring data.

My experience from work has been that not knowing what data is flowing through code is probably the biggest headache. (Javascript!). Followed by lack of compile-time guarantees. Lack of coverage of all control paths is also fairly painful. This is all pretty much summed up by one of my most common Javascript errors: `cannot read 'foo' of undefined`.

Anyways, Haskell provides solutions to all of the above in spades, but something about how it handles state in larger programs was hard for me to wrap my head around. I think that the choice of threading config/state through a large program or using a monad transformer (which I could only barely understand) were the last straws. So great for Euler Project, but hard for me personally to do other things.

## Rust

Rust seems to be more accessible for my brain, while also providing many of the guarantees that I enjoyed from Haskell. Plus it has a community geared towards beginners and has great tooling for development.

Since I like challenges, I also enjoy that Rust has it's own difficult high-level concept: memory management without garbage collection. Or, let's say it's memory management done mostly at compile time. That means that in code, I need to know a lot about how long variables live, and how I can borrow them. Fun!

Anyways, long story short, I think that Rust is great for me now, and I can see it carrying me a long way in my career. Itsatisfies my need to tweak, safely. It has enough conveniences that it doesn't feel like I'm writing C. (It's more like a verbose Python). It has my favorite high-level concepts from Haskell (data types, type inference, higher-order functions). And it has brackets! Who knew, my time in Javascript has taught me to love brackets.

I still love Haskell, though, and hope that there will be a time I'll get back to it in the future when I'm more experienced.

## Learning, Rust

So, learning Rust for real this time. Which has also corresponded with leveling up in programming in general.

Over the last 3/4 of a year, I started a new job mostly programming in node.js. I'd say that, besides learning node and js, the biggest thing it gave me was the ability to navigate and debug large projects. However, I didn't really get to practice my chops on creating my own projects, or working on harder problems (or even simply trying to get more performance from my own code).

In November, I decided that I really wanted to invest more time in my coding skills. I still love work, but it would simply not give me enough practice to get to the next level. My plan was to code at a cafe every morning before work, starting at 7am. (Turns out I'm so productive at this time, now that I can actually wake up this early!).

I think that this simple habit has actually done the most for my coding skills. In the previous months, it had been hard to code even 2 hours a week, and now I can easily get 9-10 hours a week.

An additional help was getting good materials (which of course require regular practice to get the most out of!).

My Rust journey restarted, I think, when I watched one of Steve Klabnik's talks on concurrency in rust. I watched once, got excited, then tried to do the tutorial myself, then watched again. Hooked!

Since then, I also went to a wonderful Rust Meetup taught by Niko Matsakis, which covered similar material but with more depth and some different idioms.

Realizing I needed some easy exercises to get moving, I did Code Kata and Advent of Code.

Bigger projects: I wanted to port some known projects to give me some baseline, so I tried wscat and my own slackbot.

I think the bigger projects were great for doing some struggling. But the small exercises were great for getting some of the basics down.

And along those lines, Learning Rust with Entirely Too Many Linked Lists was a great catalyst recently. After figuring out my own way of laying out programs and parsing using Advent of Code, I found out some more idiomatic ways with this tutorial. It was great to get more familiar with a library setup, as well as using pub, impl, iterators, lifetimes, and take(). I didn't fully grock some stuff like Rc, RefCell, but it's there when I need it! I literally typed my way through the entire tutorial, loved it all.

Overall: I just wanted to put down some of the resources that have been great for me learning recently, at a time when I feel like I'm doing really well. Lots of small exercises to ingrain some basics and as a starter for hard days, getting some feedback by going through some tutorials for some more idiomatic usage of Rust. Then pushing against some bigger projects (but not too big, and starting by porting).

Oh yeah, I also stopped reading hackernews.

My latest: just started on porting tinydb from Python. I already implemented my own LRU cache!
