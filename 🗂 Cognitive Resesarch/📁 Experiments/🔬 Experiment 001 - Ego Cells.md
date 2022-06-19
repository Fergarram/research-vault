%%`@TODO`
[ ] Work on a different version of the current program where each cell is not in every layer.
%%

%%`@NOTES: Concluding this experiment`
- Cellular Automata Tissue as attractor mechanism (attractor being markdown syntax)
- Custom cell types and pre-wiring give tissue super powers
- Code pipeline for working with OpenCL
- No implemente ray-casting (por performance aunque no tengo evidencia)
- Lo importante es definir el problema a resolver o el "mundo" en que se "sobrevive".
%%

## Introduciton

[[📝 Ego Cells]] are a type cellular automata that I intend to use as a mechanism to dynamically represent complex systems.

Essentially, an ego cell's purpose is to identify itself as a part of a larger model or system to constantly update its identity based on its neighboring connections, although these connections are not necessarily always in a lattice.

So for example, an ego cell could represent a letter in a word or a word in a sentence. It could also represent a person in a group of people.


## Goals

I started this experiment with the intentions of exploring this type of CA (cellular automata). I wanted to know how feasable it was to implement a small program that converts characters in a markdown file into multiple layers of ego cells that determines which syntactical component within markdown's syntax it represents. One could "ask" each character if they are part of a heading 3 or if they are part of the URL in a link, etc.

### How does this integrate into the big picture?

Essentially I need a way to represent agent-based models that's flexible enough to implement cheaply on computers and pair with learning or genetic algorithms and other external computer programs. It seems to me that having a flexible tissue of cells that's able to determine how a raw data relates to a model is a good start.

For example, characters can be linked to words and words to named experiences. At the same time named experiences can be linked to sensations to other people to names to producing hormones to contracting muscles and so on. Following the biological analogy, this example would cover a very large set of systems that would be made of organs which would be made of different types of tissues which in turn are made of different types of cells.

Thus, this first experiment aims to explore how an software implementation would look like that follows this train of thought with which a [[📝 Cognitive Architecture]] could be implemented.


## Summary

By using pre-connected cell lattices and custom cells one can solve a categorization problem within a world, in this case a finite spatiotemporal world.


## Problems

What I came to realize is that my mental model of markdown has some weaknesses — it's not as rigid as I thought. This complicated my process but at the same time it showed me how rigid models depend on hard non-overlapping rules.

In my mental model, there's a high-level representation of markdown syntax which consists of the output it generates: headings 1 to 6, paragraphs, links, etc. I know that a heading 1 starts with a hash for example.  But when it came to the feature-level of rules, I found myself improvising or rather discovering the neighboring rules as I set myself to do so.

What this means is that I came up with neighboring rules via trial-and-error only to figure out there could be a ton. I could argue that the high-level representation is based on my direct experience of the output or the actual rendering of the output HTML — Everything is text, Headings are big and vary in size, links are blue and clickable, lists have indentation and bullet points, code has a colored background, etc.

I've been trying to map a visual representation (rendered HTML) into a symbolic representation with specific syntactical rules which I did not permit myself to be fully strict about (like a real parser would).

What I suspect is that we are always trying to figure out the low-level or "feature" details about our high-level models. Constantly re-evaluating them. This is where learning or genetic algorithms could play a role.

What I've also realized is that there's a million ways to solve the same problems. Using the specific cell types I developed and the neighboring rules I came up with are just one of many possible solutions. It's up to selection to find the most optimized one for the situation or world where it exists.

For example, I initially thought that some kind of memory would be needed to keep track of the heading level (1..6) considering that each cell can only access their direct neighbors. But then realized that it could also be solved by some kind of ray casting cell — if the right most `#` cell can raycast to the left asking something about them than it can infer something about itself.

## Spatial frameworks for modeling spatial systems

While I was working on this experiment I was also reading papers such as [[📑 "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta]]. This paper proposes a framework for model-making that's based on the spatial properties and representations of objects in time. This research is based on humans and other animals which exist in and perceive this three-dimensional and physical world. I'm bringing this up because I couldn't help myself but come to hypothesize that for a 2D world made up of symbols in a grid, there has to be a similar approach that requires some analogous form of 2D grid cells, which takes me back to the previous paragraph where I mentioned a kind of coordinate system.

My new theory is that there has to be a similar framework for strictly two-dimensional grid-based spaces which requires the existance of multiple cell types or cell interactions. A universe's number of spatial dimensions and laws would determine how such a framework would be used.

In this experiment's case, there are a few ideas I have in regards to defining a spatial framework for representing information about systems within this bi-dimensional world of markdown.


## Cell types and preconnections

Ego cells can have subtypes that are connected differently in the tissue, there are a few other helpful cells that are preconnected to them.

### Character cells (Ego Cell)

### Token cells (Ego Cell)

### Line cells (Ego Cell)


### Memory and sequential patterns

Compared to spatial pattern recognition which is what the ego cells are currently doing, sequential pattern recognition presents itself as another essential building block.

Initially, I thought that some kind of memory was going to be needed to keep track of scopes (i.e. code block content vs paragraph content). Then, I thought maybe just spatial pattern recognition would be needed to identify scopes. But after realizing that links and inline-type blocks can wrap to new lines, nearest-neighboring rules can no longer solve the problem. This makes sense though. My original assumption about parsing markdown was that only top-down pattern recognition would be needed — my own sequential reading of the text went unnoticed by myself.

This leaves me with either using a memory and/or using some kind of sequential pattern recognition cell type. I'm still not sure about how, but it's clear that since the nature of written language i.e. markdown is sequential, a cell for this would make sense to exist.


### Walls and limits — Are these place cells?

Initially, I was thinking that there shouldn't be a need to keep track of walls, but this turned out to be necessary. Raycasting means collision and a ray cannot go forever into a boundless canvas. At least mentally for me that's not the case when I look at a text file — I know it has a start and an end. This is an important concept. I don't know if or how it translates into cells but there has to be a connection.


## More about preconnected lattices

Every cell is preconnected through a lattice. Those neighboring connections represent the basis of their spatial interactions. In the same way, cells need to be preconnected through a string representing sequence or time. Walls and/or corner cells would work similarly.

Since one of the limits I set for this experiment was to not use absolute coordinates as data available to cells, they instead have connections to cells representing important relative information about their position in space, time and any other dimension that could be needed.

Lattices function as some kind of organ tissue. The function of the organ in this analogy would be to parse markdown or anything else that can be represented spatially and sequentially within a grid.


## General ideas (rename this heading)

I think that more experiments will lead to discovering more patterns about how to represent and store information in transparent human semi-readable way. I have a feeling that all models are based on low-level spatiotemporal relationships between feature cells. The higher up the less "tangible" things are. I could be wrong but this is a feeling I have.

I'm also very interested in the "self-modifying" aspect of this approach. What I mean by that is, I'm interested in creating a system that can determine the preconnections of a tissue based on a given problem. I think this is where the real magic happens.

## Learning

There might be an approach where I'm able to create an algorithm that finds the correct neighboring rules automatically through an evolutive approach where it finds the best neighboring rules. The cool thing would be that the generated neighboring rules would be human-readable.

## Best-effort Computing?

Instead of trying to find a perfect combination of rules, with the new if-else situation, I can actually focus on making it robust. This could also be helpful for the learning mechanism.

%%`@NOTES: What's next`
I'm probably gonna need to finish the whole experiment and walk through the code in a video format before publishing this.

This experiment being the first one sure overwhelmes me. But it makes me happy to see a path, blurry but there it is.

I don't really know where to move next. I think it would be to implement spatial and temporal raycasting cells. But I need to develop the conceptual cell for that.

I also need to remember to mention my reasoning behind the limits I'm setting and show that cell dendrite diagram I made.

--

So, after a few weeks or days of nothing, I think the main problem is that I don't have a clear way of negating. For example, using else conditions to set layer values in OpenCL C lang.
%%

In theory this system would allow for error detection mechanisms. But that would be proven later on a different experiment probably.

## Conclusion



---

Vault Relationships:

- [[🧩 Spatiotemporal or Network or Social Awareness]]
- [[🧩 Time Perseption]]
- [[🧩 Runtime Modeling]]