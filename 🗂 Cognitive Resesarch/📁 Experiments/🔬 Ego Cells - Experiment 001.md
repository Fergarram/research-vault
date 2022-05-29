
## Introduciton

Before I explain what this experiment is about, let me tell you about a type of neuron that I'm calling "Ego Cells". Essentially, an ego cell's purpose is to identify itself as a part of a larger model or system to constantly update its identity based on its surroundings.

So for example, an ego cell could represent a letter in a word or a word in a sentence. It could also represent a person in a group of people. The main idea behind this type of cell is that it will constantly verify if its identity is correct based on its input and the relationships and interactions with neighboring cells.

In other words, ego cells serve as a way to infer conclusions about raw data in relation to a model of a system. You can read my raw ideas about ego cells in my [research vault](https://github.com/Fergarram/research-vault) if you're brave.


## Goals

I started this experiment with the intentions of discovering general observations, patterns or flaws about my concept of this type of cell. I wanted to know how feasable it was to implement a small program that converts each character in a markdown file into an ego cell that determines which high-level component within markdown's syntax it represents so that one could "ask" each character if they are part of a heading 3 or if they are part of the URL in a link, etc. This would be done using neighboring rules similar to how Conway's Game of Life works.


## Problems

What I came to realize is that my mental model of markdown has some weaknesses — it's not as rigid as I thought. This complicated my process but at the same time it showed me how rigid models depend on hard non-overlapping rules.

{`@NOTE: What's a non-overlapping rule?"`}

In my mental model, there's a high-level representation of markdown syntax which consists of the output it generates: headings 1 to 6, paragraphs, links, etc. Those are HTML elements and I know how they look when written in markdown syntax and what their intentions are within the scope of human communication. But when it came to the feature-level of rules, I found myself improvising or rather discovering the neighboring rules as I set myself to do so. What this means is that I came up with neighboring rules via trial-and-error only to figure out there could be a ton. I could argue that the high-level representation is based on my direct experience of the output or the actual rendering of the output HTML — Everything is text, Headings are big and vary in size, links are blue and clickable, lists have indentation and bullet points, code has a colored background,etc.

What I suspect is that we are always trying to figure out the low-level or "feature" details about our high-level models. Constantly re-evaluating them. This is what ego cells are for. But ego cells are not the whole system. There's obviously a very important part which is the process by which the system learns and "thinks" about new rules which then goes and validates.

I've been trying to map a visual representation (rendered HTML) into a symbolic representation with specific syntactical rules which I did not permit myself to be fully strict about (like a real parser would).

What I've also realized is that there's a million ways to solve the same problems. This ego cell approach is one of many possible solutions. It's up to evolution and selection to find the most optimized one for the situation or world where it exists.

There can be multiple mechanisms to represent solutions for specific problems such as being able to know from the top to bottom what should a heading content be. In other words, to go from "There's a heading 4" to `#### Heading content`. For example, I initially thought that some kind of memory would be needed to keep track of the heading level (1..6) but then realized that it could also be solved by some kind of coordinate system — if the right most `#` cell can raycast to the left asking something about them than it can infer something about itself.

{`@NOTE: This might be a good place to put a real code or an image.`}


## Spatial frameworks for modeling spatial systems

While I was working on this experiment I was also reading papers such as [[📑 "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta]]. This paper proposes a framework for model-making that's based on the spatial properties and representations of objects in time. This research is based on humans and other animals which exist in and perceive this three-dimensional and physical world. I'm bringing this up because I couldn't help myself but come to hypothesize that for a 2D world made up of symbols in a grid, there has to be a similar approach that requires some analogous form of 2D grid cells, which takes me back to the previous paragraph where I mentioned a kind of coordinate system.

My new theory is that there has to be a similar framework for strictly two-dimensional grid-based spaces which requires the existance of multiple cell types or cell interactions. A universe's number of spatial dimensions and laws would determine how such a framework would be used.

In this experiment's case, there are a few ideas I have in regards to defining a spatial framework for representing information about systems within this bi-dimensional world of markdown.


### Raycasting and other cell type/features

One of the cell interactions that I think of more and more is raycasting — it consists of asking the cells in a given direction to answer a specific question. For example, "From here to the top limit, is there a collision with an L3 SNIP_START?"

{`@NOTE: That example above is quite technical unless provided code examples.`}


## Memory and Sequential Patterns

Compared to spatial pattern recognition which is what the ego cells are currently doing, sequential pattern recognition presents itself as another essential building block.

Initially, I thought that some kind of memory was going to be needed to keep track of scopes (i.e. code block content vs paragraph content). Then, I thought maybe just spatial pattern recognition would be needed to identify scopes. But after realizing that links and inline-type blocks can wrap to new lines, nearest-neighboring rules can no longer solve the problem. This makes sense though. My original assumption about parsing markdown was that only top-down pattern recognition would be needed — my own sequential reading of the text went unnoticed by myself.

This leaves me with either using a memory and/or using some kind of sequential pattern recognition cell type. I'm still not sure about how, but it's clear that since the nature of written language i.e. markdown is sequential, a cell for this would make sense to exist.

`NOTES TO MYSELF:`
```
The current problem is recognizing the fact that I need sequential cells to fully represent my internal model of markdown.

The problem comes down to that — be able to abstract the problem of parsing markdown into the tempo-spatial mechanisms that allow for processing that information into relevant conclusions about that data.
```

{`@LOST: I'm probably gonna need to finish the whole experiment and walk through the code in a video format before publishing this.`}

---

Vault Relationships:

- [[🧩 Spatial or Network or Social Awareness]]
- [[🧩 Time Perseption]]
- [[🧩 Runtime Modeling]]
- 