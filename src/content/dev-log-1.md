---
title: 'Dev log 1: Tech Stack'
preview: 'Obviously, I just use whatever sounds cool'
date: 2024-07-07
---

Most of the web based stuff I have worked with has been pretty standard "modern" web-dev: client heavy JavaScript frameworks like React and Vue (altho usually with TypeScript), OOP languages like Java or C# for server stuff, following an MVC framework (dotnet or spring) and use whatever for the database. If I'm feeling lazy, and commit to "JavaScript for everything". Not to say I haven't used other stuff for projects, just that this is what I tend to gravitate to.

For this project tho, I'm trying something a bit outside of my comfort zone. The stack I'll be using Ive dubbed the SHADY stack.

## Will the real slim SHADY please stand up

### SQLite3

Honestly, I am using SQLite mostly out of convenience. 
Theres a wonderful open source index for podcasts out: the project 
[PodcastIndex](https://podcastindex.org/) which offers an API but also a SQLite database of their index. This combined with Django's ORM being defaulted to SQLite makes it a pretty easy default to go with.

That said, every time I have used SQLite, I have been consistently surprised by it. The fact that such a powerful tool that allows for stuff like full-text search, thats reasonably fast.  

It may not be the most scalable, but considering the user base for this project is probably gonna be 3 (me, myself and I), I think it'll do just fine. That said, SQLite also isn't the main database I plan on using. Im mostly using it for the indexing value, which I think might mitigate some of the performance impacts.

### HTMX

I hate React. 

Ok that might be a bit too strong, but I have grown to be annoyed at React and Vue. I have a decent amount of experience in it (like every other dev and their mom) and while React does have a great dev experience, I have grown a bit weary of trying to shove everything on the client machine. Especially whenever I'm writing something small, React always felt like using a professional kitchen to make smores. 

Then I discovered HTMX. After around 4 years of setting up more hooks than a fly fishing tournament and stressing about the virtual DOM, the sheer simplicity of "just ask the server and modify the client slightly" was so eye widening i was worried they would fall out of my skull. That said, I haven't used - this will be my first use of the tool outside of play examples ripped from the documentation. That said, having seen what others have done with it, I'm excited to use it for this project.

### AlpineJS

Im choosing AlpineJS for similar reasons as HTMX. Having tired of react for a bit, i decided I want to try something different for this project. Alpine - from the outside anyway - seems like 90% of the library is syntactic sugar for `document.getElementByID` and `addEventListener` in html tags, but tbh thats probably all that I need for the moment. ~~And because JQuery doesn't make the stack into a cool acronym.~~    

### Django

After deciding to go with Alpine and HTMX, I could have gone with something like Express for the web server. But in keeping with the spirit of trying new things, I've decided to go with Django. From what I've read online, it seems to go really well with HTMX and Alpine, plus I really like how organized the file structure layed out. The way it also handles the ORM and database migration also feels like it will come in handy if I need to jump ship from SQLite too. Altho, one small downside is the ORM wont work with the main database I plan to use which is:

### YottaDB

From what I assume, all the other technologies in the stack have pretty high name recognition. Not this one. And if you do know, you might be cringing out of your mind.

[YottaDB](https://yottadb.com/) for those not in the know is a modern implementation of MUMPS. MUMPS for those who don't know is part database, part programming language created in 1966 for Massachusetts General Hospital. The language is quite archaic, the only datatype in the language is a string, [has the readability of assembly](https://github.com/programarivm/mumps-examples/blob/master/06-databases/basic-sql-crud/Main.m), has an inability to use recursion, and is only used in electronic medical records and banking tech stacks by legacy companies at this point.

So now you might be horrified and wondering "Why on earth would you ever use MUMPS for a backend in the year 2024??". Well first off, YottaDB is slightly different to MUMPS in a few key ways. But to the point - I made it seem like the worst thing every, I actually feel really strongly about using MUMPS (and YottaDB in particular), so much so that I'm going to go into it in a [further dev log](/dev-log-2), but the TLDR is this:

MUMPS (*and YottaDB in particular*) is ***100%*** a sleeper. It's performance numbers alone easily make a case for replacing any NoSQL database currently in use with it.

Any online discourse you find about it makes it seem like its akin to COBOL - a decrepit language that only exists because of tech debt. But after using it daily at work and playing with it in personal code, I'm convinced its more similar to Fortran, LISP or C - an ol' reliable workhorse who's age is a byproduct to how good it is.