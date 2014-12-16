+++
Categories = ["Development", "Haskell"]
Description = ""
Tags = ["Development", "haskell"]
date = "2014-12-15T22:32:18-05:00"
menu = ""
title = "Utilities"

+++

Exciting! I wrote my first program that's for "real" work! It's a small script to upload files to an ftp server that hosts the MGA ladder.

It's kind of funny, it seems like such a simple program when I look at it now. But maybe one month ago, it might have felt very complicated in Haskell. I think that's because it helped this time around to know more about monads and >== and liftM. The steps of the script are not hard, nor was calling the libraries (for ftp, directories, etc.). But understanding what Haskell was actually doing (I think that this would be called semantics?) finally happened. 

So, a cool little program that saved me the huge annoyance of using a GUI ftp client, while also giving me some fun hands-on coding and digging in libraries, combined with furthering my understanding of Haskell abstractions like monads.

In addition, I also just realized that I can easily extend this utility for helping me convert file formats. I currently write in Markdown and convert to html using pandoc (which is written in Haskell!). I had thought that it was a pity that I couldn't call the pandoc executable from inside the script, like I might have done with a bash script.... But I can integrate the pandoc library into my library! Even more saved keystrokes coming my way! I may even be able to use this script to apply html headers/templates so that it will be easier to add css and javascript to the basic site.

Of course, eventually the full site will be database driven (Flask, or maybe even Scotty if there's enough documentation). But for now, it's fun working on this utility. Following close behind is another CLI utility to generate AGA ratings submission forms.
