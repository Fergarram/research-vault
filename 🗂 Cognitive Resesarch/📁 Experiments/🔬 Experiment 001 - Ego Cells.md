%%`@TODO`
[ ] Follow the cell specs to implement that.
[ ] Implement GA pipeline that works with OpenCL.
%%


## Introduciton

[[📝 Ego Cells]] are a type cellular automata that I intend to use as a mechanism to dynamically parse raw data as instances of complex systems.

Essentially, an ego cell's purpose is to identify itself as a part of a larger model or system to constantly update its identity based on its neighboring connections, although these connections are not necessarily always in a lattice.

So for example, an ego cell could represent a letter in a word or a word in a sentence. It could also represent a person in a group of people.


## Experiment goals

I started this experiment with the intentions of exploring this type of CA (cellular automata). I wanted to know how feasable it was to implement a small program that converts characters in a markdown file into multiple layers of ego cells that determines which syntactical component within markdown's syntax it represents. One could "ask" each character if they are part of a heading 3 or if they are part of the URL in a link, etc.


### How does this integrate into the big picture?

Essentially I need a way to represent agent-based models that's flexible enough to implement cheaply on computers and pair with learning or genetic algorithms and other external computer programs. It seems to me that having a flexible tissue of cells that's able to determine how a raw data relates to a model is a good start.

For example, characters can be linked to words and words to named experiences. At the same time named experiences can be linked to sensations to other people to names to producing hormones to contracting muscles and so on. Following the biological analogy, this example would cover a very large set of systems that would be made of organs which would be made of different types of tissues which in turn are made of different types of cells.

Thus, this first experiment aims to explore how an software implementation would look like that follows this train of thought with which a [[📝 Cognitive Architecture]] could be implemented.


## Cell taxonomy and preconnections

Ego cells can have subtypes that are connected differently in the tissue, there are also a few other helpful cells that are preconnected to them.

Defining the reach of the neighborhood or the number of abstraction layers above the raw data is determined by the problem requirements and nature.

In the case of parsing markdown, we could benefit from a larger neighborhood (so like 6 cells of radius) and maybe three layers above raw data representing lines, borders, and blocks.

Since I know the nature of parsing markdown, I can try to predict the needed reach in the tissue, not only that but also how they need to be preconnected — I'll talk about preconnections after explaining a bit more about each cell type needed to parse markdown.

I have to say that I'm not doing Token Cells since that's the job of the genetic algorithm. So instead, I think that the size of the neighborhood and the other connections will always determine which tokens are possible and make more sense to solve the problem, in this case, parsing markdown.

### Character Cells (Ego Cell)

This is the obvious cell type. We need a way to represent characters in space. They are conencted 3 cells to their left and right and only 1 cell up and down. Each is also connected to the current, top and bottom Line Cells. For representing sequence, they are connected to the previous and next cells with a reach of 3 neighbors; if the next cell is in the line above or below, it will connect to it regardless.
%% `Insert Diagram Here` %%


### Border Cells (Impostor Ego Cell)

These can pretend to be any type of Ego Cell and their value is always the same — null. Real Ego Cells are connected to them when close to the border of the tissue thinking they are "living" neighbors.
%% `Insert Diagram Here` %%


### Line Cells (Ego Cell)

These are connected to a row of Character Cells in order to represent the "line" abstraction probably needed to parse markdown.
%% `Insert Diagram Here` %%


### Block Cells (Ego Cell)

These are anatomically similar to Line Cells. Each is connected to a Line Cell and each of their sibilings. Why? Because a single or multiple Line Cells could represent a Block. For example, a paragraph vs a heading.
%% `Insert Diagram Here` %%


### More about preconnected lattices

Every cell is preconnected through a lattice. For example, neighboring connections between Charachter Cells represent the spatial interactions between the main actors. In the same way, cells need to be preconnected through in a way that we can represent a sense of sequence or time. Walls and/or corner cells would work similarly.

Since one of the limits I set for this experiment was to not use absolute coordinates as data available to cells, they instead have connections to cells representing important relative information about their position in space, time and any other dimension that would be needed.

We want to have preconnected tissue in order to be specific about the type of space or substrate that it's going to be sovling problems in.


## Using genetic algorithms

This experiment is divided into two sections:

1. designing and developing a system that allows Ego Cells to exist and;
2. implementing a genetic algorithm that based on training data, it can learn to find the best neighboring rules that correctly parse markdown.

This article you're reading corresponds to the first part. The second part is soon to be published.


%%` @NOTES: Memory and sequential patterns` 
Compared to spatial pattern recognition which is what the ego cells are currently doing, sequential pattern recognition presents itself as another essential building block.

Initially, I thought that some kind of memory was going to be needed to keep track of scopes (i.e. code block content vs paragraph content). Then, I thought maybe just spatial pattern recognition would be needed to identify scopes. But after realizing that links and inline-type blocks can wrap to new lines, nearest-neighboring rules can no longer solve the problem. This makes sense though. My original assumption about parsing markdown was that only top-down pattern recognition would be needed — my own sequential reading of the text went unnoticed by myself.

This leaves me with either using a memory and/or using some kind of sequential pattern recognition cell type. I'm still not sure about how, but it's clear that since the nature of written language i.e. markdown is sequential, a cell for this would make sense to exist.
%%


%%` @NOTES: Walls and limits — Are these place cells?`
Initially, I was thinking that there shouldn't be a need to keep track of walls, but this turned out to be necessary. Raycasting means collision and a ray cannot go forever into a boundless canvas. At least mentally for me that's not the case when I look at a text file — I know it has a start and an end. This is an important concept. I don't know if or how it translates into cells but there has to be a connection.
%%

%%`Spatial frameworks for modeling spatial systems`
While I was working on this experiment I was also reading papers such as "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta (linked at bottom of this page). This paper proposes a framework for model-making that's based on the spatial properties and representations of objects in time. This research is based on humans and other animals which exist in and perceive this three-dimensional and physical world. I'm bringing this up because I couldn't help myself but come to hypothesize that for a 2D world made up of symbols in a grid, there has to be a similar approach that requires some analogous form of 2D grid cells, which takes me back to the previous paragraph where I mentioned a kind of coordinate system.

My new theory is that there has to be a similar framework for strictly two-dimensional grid-based spaces which requires the existance of multiple cell types or cell interactions. A universe's number of spatial dimensions and laws would determine how such a framework would be used.

In this experiment's case, there are a few ideas I have in regards to defining a spatial framework for representing information about systems within this bi-dimensional world of markdown.
%%

%%`@NOTES: Problems`
What I came to realize is that my mental model of markdown has some weaknesses — it's not as rigid as I thought. This complicated my process but at the same time it showed me how rigid models depend on hard non-overlapping rules.

In my mental model, there's a high-level representation of markdown syntax which consists of the output it generates: headings 1 to 6, paragraphs, links, etc. I know that a heading 1 starts with a hash for example.  But when it came to the feature-level of rules, I found myself improvising or rather discovering the neighboring rules as I set myself to do so.

What this means is that I came up with neighboring rules via trial-and-error only to figure out there could be a ton. I could argue that the high-level representation is based on my direct experience of the output or the actual rendering of the output HTML — Everything is text, Headings are big and vary in size, links are blue and clickable, lists have indentation and bullet points, code has a colored background, etc.

I've been trying to map a visual representation (rendered HTML) into a symbolic representation with specific syntactical rules which I did not permit myself to be fully strict about (like a real parser would).

What I suspect is that we are always trying to figure out the low-level or "feature" details about our high-level models. Constantly re-evaluating them. This is where learning or genetic algorithms could play a role.

What I've also realized is that there's a million ways to solve the same problems. Using the specific cell types I developed and the neighboring rules I came up with are just one of many possible solutions. It's up to selection to find the most optimized one for the situation or world where it exists.

For example, I initially thought that some kind of memory would be needed to keep track of the heading level (1..6) considering that each cell can only access their direct neighbors. But then realized that it could also be solved by some kind of ray casting cell — if the right most `#` cell can raycast to the left asking something about them than it can infer something about itself.
%%


## Concluding observations

%%`@NOTES: Concluding this experiment`
- Cellular Automata Tissue as attractor mechanism (attractor being markdown syntax)
- Custom cell types and pre-wiring give tissue super powers
- Code pipeline for working with OpenCL
- No implemente ray-casting (por performance aunque no tengo evidencia)
- Lo importante es definir el problema a resolver o el "mundo" en que se "sobrevive".
- Talk about problems and other ideas? Or promote my wiki so that they can read my personal notes?
%%

---

Vault Relationships:

- [[🧩 Spatiotemporal or Network or Social Awareness]]
- [[🧩 Time Perseption]]
- [[🧩 Runtime Modeling]]

- [[📑 "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta]]