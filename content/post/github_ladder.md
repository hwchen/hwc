+++
Categories = ["Development", "Git", "Github"]
Description = ""
Tags = ["Development", "git", "github"]
date = "2015-01-04T18:31:24-05:00"
menu = ""
title = "Github and Ladder"

+++
Today, my friend Andrew was kind enough to take me through some of the basics of Git and Github.

For the MGA ladder, we're going to set up some software to help manage recording and displaying of results. Hopefully, we'll also get automatic submission of rated games to the AGA.

I've already written some [utilities](https://github.com/hwchen/ladder-hs) in Haskell to automate updating of the ladder site, using a markdown -> pandoc ->html -> upload to site. So what used to take me 5 minutes now only takes me less than a minute! Maybe not that much absolute time saved, in the grand scheme of things, but I savor every keystroke I save (and especially point and clicks).

The software that Andrew and I are starting will eventually be much more ambitious. Instead of working just on flat files as a data store, and manually running a program to convert results to a website, we'll be using flask to set up a web framework with a database.

Today's first major step was to get a workflow so that we could cooperate on the project. Github is one of the go-tos for collaboration, but it's pretty complicated for a novice. Fortunately, Andrew has a lot of experience with Git for his sofware engineering work. I learned about forking, the difference between upstream and origin (and master), and how to use branches. We stepped through our planned workflow:

1. Create local branch
2. Commit and push local branch to origin branch
3. Pull request from origin branch to upstream master (currently massgo/mgaladder)
4. After review and merge, then merge changes back to origin and local masters (in whatever preferred order).

So, a lot for my brain to take in today. Git is very powerful and flexible, and lots of thanks to Andrew for his help. I don't think I could have figured this out in even a day on my own, and we spent just one hour.

I can see why Git experience in particular is a highly requested skill for software developers. It's not just a "version control" (in perhaps the back-up sense), it's a very powerful coordination software that makes very large engineering projects possible.
