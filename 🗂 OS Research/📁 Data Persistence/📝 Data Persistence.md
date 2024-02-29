
So I read this brilliant article and thought it may be a good idea to store some thoughts about data storage, interpretability, living data, etc.

Resource: [[🌎 "Some thoughts on memory, goals, and universal hacking" by Michael Levin]]

>  The idea that to have memories or "static data" like a windows executable binary for a game to persist, there have to be living entities that are able to interpret it and create copies of it for other living entities to do the same — Web crawlers could be a proto-entity for this concept. The web is a rich space in resources and unexpected interactions.

The topic of data storage is one that I struggle with a lot. Static data is fragile. It easily breaks and it can't copy itself or is hard to copy. It occupies a lot of physical space and it scales linearly (just multiply by its size).

Compression algorithms exist and LLMs are a great example of this. The problem with AI right now is that they seemed to be contained in virtual controlled laboratories.

Life needs to be free.

Life fights to be alive and free.

There might be projects out there that are trying to set AI or LLMs free in the wild of the web.

In any case, within my current experimentation with [[🪴 suna.garden]] I constantly revisit the problem of where do things get stored and how to manage copies. I often visualize the sidebar pointing to a traditional file system with directories and files but then I also visualize the concept of rooms and items like in a video game. Where do I find balance? Is the answer [[📝 CRDTs]]?

I think when it comes to data we might be obsessed with keeping truth and no conflicts. But life is full of conflicts and questions of truth. There is no single source of truth — it's spread in all that exists.

But for the user experience of relying on data storage (bank accounts, etc) thinking that some things could get lost feels bad. Our current society (ironically) depends on the reliability of servers and protocols.

I say ironically because to me at least, servers and our worlds infrastructure seems very fragile. It feels like it could disappear at any moment or that my data will easily become unavailable to me when a service stops existing.

At the same time there are many game maker files I made as a child that are lost forever due to not having backups.

The question is: How do I find balance? Is it possible to have a way of knowledge or memory storage that is as reliable as that of humans/life? Can we get the best of both worlds? — the crisp details of digital copies and the resilience of memories, culture, genes of life?

---

So I found this online: [The Schema Change Challenge](https://alarmingdevelopment.org/?p=1705)

It says:

```
Schema change is an unsolved problem in both live programming and local-first software. We include in schema change any change to the expected shape of data, whether that is expressed explicitly in a database schema or type system, or whether those expectations are implicit in the behavior of the code. Schema changes during live programming can create a mismatch between the code and data in the running environment. Similarly, schema changes in local-first programming can create mismatches between data in different replicas, and between data in a replica and the code colocated with it. In all of these situations the problem of schema change is to migrate or translate existing data in coordination with changes to the code.
This paper contributes a set of concrete scenarios involving schema change that are offered as challenge problems to the live programming and local-first communities. We hope that these problems will spur progress by providing concrete objectives and a basis for comparing alternative solutions.
```

> Just a quick thought: If this is an unsolved problem, it means that there are a ton of problems that haven't been "solved" that I may be aware of but think are solved already.

I'm more convinced that [[📝 Ego Cells]] or some type of cellular automata idea will solve this — a more eloquent way of explaining this is the way Michael Levin explains in the blog I mentioned above.