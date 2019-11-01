# The most important skill for biologist dabbling in bioinformatics

As a wet-lab person that starts to use some of the bioinformatics tools to analyse NGS data, it seems like a completely different world.
Unless you have an IT support team, chances are, you're likely to have to install some of the tools for your own use.
And if you never tried before, the most frustrating is that part where you can't even begin you analysis yet. Yes, that is the tool installlation itself.
Perhaps it's like what stated in Murphy's law, " whatever can go wrong, will go wrong".

Different types of error, compiling error, missing libraries, missing dependencies. One after another that cropped up that make even the 
installation of tool itself difficult, let alone starting the analysis.
Spending days after days (okay, perhaps I'm the one that is slower in catching up) frustrated at the idea that you can't even complete a simple program installation,
even doubting yourself.

The most important skill I found important in troubleshooting this kind of error is **knowing how to read error message**.
When I just starting out (although I'm still quite new), I used to just copy and paste the error message in Google and try to read comments and
suggestion from forums (biostar, seqanswer, stack overflow) and try them out one by one, which often take days to finally manage to install
the program.

Over time, I realised that if you know how to read the error message, where it is usually the first error that pop up is the crux of the problem.
e.g. missing library, segmentation fault, cannot locate xxx, failed to make xx/src.
If you can identify the main problem right early, the work left then is just googling how to install that specific library or updating the
dependency, and voila, the installation works finally (although in my case I still usually don't know how or why it works anyway).

So, trace back to the first error message and look out for keywords before the error message, usually "missing xxx", "cannot locate xxx", 
and hopefully it will help locating the problem causing element earlier.
