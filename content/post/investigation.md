+++
Categories = ["Development", "Rust", "Haskell"]
Description = ""
Tags = ["Development", "Rust", "Haskell"]
date = "2014-10-25T13:35:22-04:00"
title = "Investigation, Haskell and Rust and Job Search"

+++

Since my last post, I've been doing a lot of investigating. I could have jumped even
further down the Python rabbit hole by immediately trying to start on projects. I think
two things stopped me: one, that I didn't have a pressing need that I could address with
a project, and two, that my brain was telling me it wanted to explore more what
programming could mean. The result was a foray into Haskell.

#### Haskell
Haskell is described as a lazy, functional language that has a very strong notion of
purity. Great explanations of the language can be found at haskell.org.

I had messed around with Learn You a Haskell, a great introductory book, but had not
really gotten a grasp on the language. I decided to work through CIS194, a class on
Haskell taught by Brent Yorgey at UPenn, with all materials online! The exercises ended
up being at a great level for me (similar to Think Python). I've currently worked through
the midway point, right before things get abstract.

I think that, coming from Python, my greatest delights were:

- Exteremely clean syntax
- Algebraic Data Types!
- Maps, filters and folds

I've found that for me, the syntax makes it really easy to see the structure of the
program. Visual noise takes away from shape, and I'm extremely shape-oriented (as I know
from playing Go).

The Algebraic Data Types (ADT) were a revelation in terms of rethinking how to organize
programs. For me, they make a lot more sense than what I know about classes and OO
programming. ADTs in Haskell are strict but extremely expressive, and can tell you so
much about the shape of a program up-front without delving into "details" of execution.

Of course, to operate in the real world, there needs to be a certain amount of sacrifice
of purity. In Haskell, this often has to do with I/O. I haven't gotten to really grapple
with this part yet, but I'm looking forward to it as I continue to learn.

#### Rust

Another language I looked at recently was Rust, which is a new language often compared to
Golang. I'm glad I branched out to Haskell, because I learned some things I really
enjoyed in programming (like ADT), and those things really popped out when looking at
Rust. Rust seems to be another imperative programming language in the vein of Python or
C++, but what struck me was that it had its own implementation of ADT! I wrote some toy
programs in Rust, thinking that perhaps the combination of imperative with functional
would fit my mindset really well and make programming easy. But Rust has another trick up
its sleeve: memory-safe programming, which is actually the language's main calling card.
I only know a little, but it looks like Rust places responsibility for keeping track of
when and where memory is allocated to variables, while also creating a framework so that
the compiler can help you keep track.

Thinking about memory, as well as pointers and mutability explicitly in programs, is
pretty complicated above just making my program run. Python basically took care of it all
for me, with some cost in terms of performance, structure, and safety. Haskell takes care
of those things to, but in part by limiting the programming paradigm. The more technical,
close-to-the-metal stuff hurts my head a bit, and was definitely one of the reasons I
found programming hard in high school and college. (glad I was reintroduced through
Python!). But I'm glad to know what's possible in a programming language.

#### Investigations

I want to keep investigating both Rust and Haskell. I guess it'll be a little bit of
juggling as I also want to learn Python. But it does seem to me that picking up a bit of
syntax or learning a new language is not too hard for very basic competency (especially C
related languages like Rust or Python). I've done it a few times now, with these
languages and also Java and Turbo Pascal in the past. 

The real challenge for me is not being fluent in the "syntax" of the language, but to
learn how to construct programs. Right now, I don't know how much of this will relate to
the idioms of each language (the structure of a Haskell is different in certain ways from
a Python program). But I do know that learning different idioms is good. In fact,
learning Haskell is one recommended way of getting better at Python (or even programming
in general).

In any case, I'm going to keep plugging away and finding bigger projects, whatever they
may be. Currently on my radar are a toy browser engine in Rust, some exploration of AGA
ratings, some graphing for a nonlinear dynamics class, and hopefully some fun small project
in Haskell. I won't try to go too big; I know that I need to build lots of small projects 
first.

### Job Search
So does any of this have to do with a job search? After all, I'm not building my skills
in a pattern that necessarily makes it obvious to future employers that I'm getting
better. I've been told quite a few times that it's important to have projects to show,
especially for somebody who is self taught.

I guess I wanted to give myself something to aspire to. While web development in and of
itself isn't necessarily a boring job, I wanted to know a little better what it would
take to tackele interesting computational problems, whether in web development or in
another industry. I didn't want to just aim for patching together frameworks.

I'm still glad I took the time to look around at the landscape and dig into some
fundamentals (I implemented binary trees in Haskell!). I know it will serve me well in
the future to have a broad outlook even at the beginning. I just have to keep going so I
can build skills that will actually be useful to employers, while also maintaining my
enthusiasm.
