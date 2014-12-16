+++
Categories = ["Development", "Haskell"]
Description = ""
Tags = ["Development", "haskell"]
date = "2014-12-16T00:44:44-05:00"
menu = ""
title = "Monads, Functors, and the Contents of the Current Directory"

+++

While trying to get the contents of the current directory in a small Haskell script, I inadvertantly put together some cool connections about Monads and Functors. (disclaimer: this is not a Monad tutorial. Also, beware of ugly code and circuitous reasoning).

The basic idea was to `STDOUT` the contents of the current directory. Pretty simple? In Haskell pseudocode, I thought:

```
h <- getDirectoryContents getCurrentDirectory
putStrLn h
```

Basically, bind the result of the `IO` operation (get contents of the current directory) to `h`, and then print `h`. This did not work on many levels.

Before moving on, I'm going to change the syntax to:

```
getDirectoryContents getCurrentDirectory >>= putStrLn
```

The >>= operator may look a little strange. As I was just learning more about Monads, I was excited to try this syntax, it basically binds the result on the left directly to the right side, so the right side can be applied to it. This means that the intermediate step of binding to `h` in the above example is skipped.


#### Troubleshooting and Types

Ok, now that the preliminary is out of the way, why didn't my function work? Let's look at the types.

```
getDirectoryContents :: FilePath -> IO [FilePath]

getCurrentDirectoy :: IO FilePath

putStrLn :: String -> IO ()
```

`FilePath` is an alias for a `String`. That's pretty straightforward. But what about IO? For me, it was easiest to think of it as a "container" or "computational context." Because Haskell tries to stay pure, it keeps its Input Output computations in a separate context from "pure" functions. 

This idea of a context for values has really helped me understand some of the abstractions of Haskell. For example, a functor is kind of like a container that has the property that you can transform the value inside without affecting the container. This property is expressed in the fmap function, which applies a function to a value (or values) inside of a "box". `fmap` can transform integers in a list, or a string inside a `Maybe`, or even a string inside of `IO`!

`IO` also happens to be a Monad, another abstraction built around the idea of a "container." This time the container encapsulates values and sequences of computations (which appears kind of like imperative programming). With my shallow understanding, I hope I'm not too wrong. In any case, in order to access a value inside a Monad like `IO`, you need to "reach inside," which is the idea behind `h <- getDirectoryContents "/"` By binding the value that was in the IO context, you can work on that value with pure functions.

#### Piecing things together

Ok, now knowing the basic structure of how things fit together, I needed to actually put it together.


`getDirectoryContents` takes a `FilePath` as an argument, but `getCurrentDirectory` returns an `IO FilePath`. They don't match! so what should I do? I just realized now that I could have used `<-` or `>>=` to bind the value inside `IO FilePath`. But I had learned something fancier last night, `liftM`! And I wanted to use it! I knew that I could "lift" the function into the Monad context, so that it could operate on a value enclosed in a Monad (like IO). So I did, and it worked great, except now there was a nested monad.

```
liftM getDirectoryContents getCurrentDirectory :: IO(IO [FilePath]))
```
When I tried to bind the above code to any function, it wouldn't work because of the nested IO!

But this ugly version would work (you can see the nesting):

```
h' <- liftM getDirectoryContents getCurrentDirectory
h <- h'
putStrLn h --This line doesn't actually work but I'll explain later
```


#### Diversion into functors (it all comes back)

So, as part of this long rambling story, I happened to be reading about functors tonight and decided to explore using fmap to do some simple CLI string manipulation, like so:

```
main = do
    fmap reverse getLine >>= putStrLn
```

I decided to search and see if I could find an example I remembered of an infinite loop of input and output. Something like `interact`. But in my search I came across a [Stack Overflow](http://stackoverflow.com/questions/5216473/why-doesnt-putstrln-getline-work) question. In the answer, I saw that the reverse bind `=<<` is equal to `fmap` followed by `join`. My reaction was great surprise!

By looking at types, I figured out the `fmap` part, but still wasn't sure how using `join` would get the correct type result. So I looked it up on Hoogle, and I found out that `join` removes a level of monadic structure! And that was exactly what I had been looking for earlier today!


#### Back to the Main Thread

So, the problem of getting rid of the nesting was solved with join!

```
join (liftM getDirectoryContents getCurrentDirectory) :: IO [FilePath]
```

Now I could bind it to a function using the `>>=` operator. But notice that since the type of the argument would be `IO [FilePath]`, I can't just use `putStrLn`, which takes a `String` and not a `[String]`. What I'd like to do is map the function `putStrLn` to each of the values in `[FilePath]`.

Normal `map` won't work to print. I guess I'm not completely clear why, but I think that using `map` doesn't actually evaluate the monad (in this case `putStrLn`). `mapM` maps and also evaluates and also returns a result. `mapM_` is more appropriate for this case of just printing, where return value is not needed, since it maps and evaluates but doesn't return.

#### Final Code

So a long-winded and long-winding road to get to the final code:

```
join (liftM getDirectoryContents getCurrentDirectory) >>= mapM_ putStrLn
```

It's probably more cryptic than, say, a typical Python implementation. But it has its own beauty, that comes from understanding the abstractions and the building blocks that come together to build this piece of code. It fits together kind of like Legos.

I think that after this little excursion, and my attempt to write it up, I'll be able to read a lot more example code! And this was much more fun to me than trying to work through a monster assignment on functors and monads. Start small!


#### Last lessons

```
getCurrentDirectory >>= getDirectoryContents >>= mapM_ putStrln
```

Hmmm... a lot simpler and more elegant, right? Still, I think I learned more by doing it another way first, just because it was what I was thinking at the time. And I had a fun excursion, trying to apply `liftM`. Now I know `liftM` and `join` are together like `>==`.

Puzzling through like this is fun, but I also see that it required a decent bit of knowledge already. I guess it's just hard (and fun) to be a beginner.

Any mistakes in understanding on my own, feel free to let me know if there's mistakes! This is not meant to be a teaching tool, but rather a place for me to think about how Haskell works! I'm practicing my writing skills too, practice makes perfect! (or at least better?)
