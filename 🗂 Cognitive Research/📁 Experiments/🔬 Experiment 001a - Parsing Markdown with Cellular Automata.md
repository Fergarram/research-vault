---
description: An implementation of Ego Cells, a type of cellular automata that parses Markdown semi-asynchronously based on neighboring rules.
---

%%
Note that this experiment is not finished yet.

---

I'm currently looking at three parts:

Part 1 - The initial truth model
Part 2 - The instancing mechanism - ego cells
Part 3 - the neighboring rules with genetic algorithms
%%

## Github Repository

[research-experiments/ego-cells-markdown](https://github.com/Fergarram/research-experiments/tree/main/ego-cells-markdown)

---

## Clip Notes

- [[📎 Correction Cells]]
- [[📎 Analyzing the true essense of markdown]]
- [[📎 Underestimating the parsing problem]]
- [[📎 Memory and sequential patterns]]
- [[📎 Spatial frameworks for modeling spatial systems]]
- [[📎 Thinking in terms of simple programs]]
- [[📎 Walls and limits — Are these place cells?]]

---

## Introduciton

[[📝 Ego Cells]] are a type cellular automata that I intend to use as a mechanism to dynamically parse data as instances of complex systems.

Essentially, an ego cell's purpose is to identify itself as a part of a larger model or system to constantly update its identity based on its neighboring connections, although these connections are not necessarily always in a lattice.

So for example, an ego cell could represent a letter in a word or a word in a sentence. It could also represent a person in a group of people.


## Purpose

I started this experiment with the intentions of exploring this type of CA (cellular automata). I wanted to know how feasable it was to implement a small program that converts characters in a markdown file into multiple layers of ego cells that determines which syntactical component within markdown's syntax it represents. One could "ask" each character if they are part of a heading 3 or if they are part of the URL in a link, etc.


### How does this integrate into the big picture?

Essentially I need a flexible enough way to represent mental models that can be implemented cheaply on computers and paired with learning or genetic algorithms and other external computer programs. It seems to me that having a flexible tissue of cells that's able to determine how raw data relates to a model is a good start.

For example, letters can be linked to words and words to named experiences. At the same time named experiences can be linked to sensations to other people to names to producing hormones to contracting muscles and so on. Following this natural analogy, we want to be able to build cognitive organs and systems.

Thus, this first experiment aims to explore how a software implementation would look like that follows this train of thought with which a [[📝 Cognitive Architecture]] could be implemented.


## TL;DR

For as simple as markdown may seem it requires quite a few building blocks that I didn't take into account when I was initially thinking about this first experiment. Trying to find the neighboring rules needed to create this parser tissue lead me to discovering that there is an unkown number of possible building blocks that can be used to describe markdown — it's not just characters in a grid and a high-level model.

What I found out is that the high-level model is made up of other models (or building blocks) that may have derived from different sources. For example, I initially didn't think I would need to represent words as characters separated by spaces and other special characters or that parsing requires a representation of sequence. Assuming these and other things was naive but it lead to a richer headspace for me now.

The next step would be to set the bar way lower and to focus on using the tools I developed in this experiment to try to solve easier problems than parsing markdown.


## Discoveries: Cell taxonomy and preconnected tissue

Ego cells can have subtypes that are connected differently in the tissue, there are also a few other helpful cells that are preconnected to them.

Defining the reach of the neighborhood or the number of abstraction layers above the raw data is determined by the problem requirements and nature.

In the case of parsing markdown, we could benefit from a larger neighborhood (6 cells of radius) and three layers of abstraction to represent the cell's identification with special characters (a `#`) tokens (the `###`'s) and blocks (a heading level 3).

Since I know the nature of parsing markdown, I can try to predict the needed reach in the tissue, not only that but also how they need to be preconnected — I'll talk about preconnections after explaining a bit more about each cell type needed to parse markdown.

I have to say that I'm not doing Token Cells since that's the job of the genetic algorithm. So instead, I think that the size of the neighborhood and the other connections will always determine which tokens are possible and make more sense to solve the problem, in this case, parsing markdown.

### Character Cells (Ego Cell)

This is the obvious cell type. We need a way to represent characters in space. They are conencted 3 cells to their left and right and only 1 cell up and down. Each is also connected to the current, top and bottom Line Cells. For representing sequence, they are connected to the previous and next cells with a reach of 3 neighbors; if the next cell is in the line above or below, it will connect to it regardless.

%% `Insert Diagram Here` %%

`Connection Index`
```
N0..2 = Left Neighbors
N3..5 = Right Neighbors
TN = Top Neighbor
BN = Top Neighbor
PN = Previous Neighbor
NN = Next Neighbor
TL = Top Line
BL = Bottom Line
CL = Current Line
```

`Possible Self States`
```
These are the "hard truths we know" divided into 3 layers:

1. One of all characters categories or NULL (16 + 1)
2. One of all possible sub-blocks or NULL (10 + 1)
3. One of all possible blocks or NULL (9 +1)
```

Remember that a connection between cells mean they may have access to each state type if needed, so for example, between Character Cells they can read all 4 "layers" of state.


### Border Cells (Impostor Ego Cell)

These can pretend to be any type of Ego Cell and their value is always the same — null. Real Ego Cells are connected to them when close to the border of the tissue thinking they are "living" neighbors.

%% `Insert Diagram Here` %%


### Line Cells (Ego Cell)

These are connected to a row of Character Cells in order to represent the "line" abstraction probably needed to parse markdown. These cells can determine their state based on what each Character Cell tells them and each Character cell can also read the state of the Line Cell.

%% `Insert Diagram Here` %%

`Connection Index`
```
C0..127 = Character Cells within the row
```

`Possible Self States`
```
1. One of all possible blocks or NULL
```


### Block Cells (Ego Cell)

These are anatomically similar to Line Cells. Each is connected to a Line Cell and each of their sibilings. Why? Because a single or multiple Line Cells could represent a Block. For example, a paragraph vs a heading.

%% `Insert Diagram Here` %%

`Connection Index`
```
L = Line Cell within the same row
TB0..126 = Every other Block Cell from top to bottom ???
```

`Possible Self States`
```
1. One of all possible blocks or NULL
```

At the time of writing this, I'm not sure if both Block Cells or Line Cells are needed since they do pretty much the same thing.


### More about preconnected lattices

Every cell is preconnected through a lattice. For example, neighboring connections between Charachter Cells represent the spatial interactions between the main actors. In the same way, cells need to be preconnected through in a way that we can represent a sense of sequence or time. Walls and/or corner cells would work similarly.

Since one of the limits I set for this experiment was to not use absolute coordinates as data available to cells, they instead have connections to cells representing important relative information about their position in space, time and any other dimension that would be needed.

We want to have preconnected tissue in order to be specific about the type of space or substrate that it's going to be sovling problems in.


## Problems

To get to the state of this publication, I had to try different ideas in paper and code, educate myself more on the topics of complexity and cellular automata.


## Concluding observations

- Cellular Automata Tissue as attractor mechanism (attractor being markdown syntax)
- Custom cell types and pre-wiring give tissue super powers
- Code pipeline for working with OpenCL
- No implemente ray-casting (por performance aunque no tengo evidencia)
- Lo importante es definir el problema a resolver o el "mundo" en que se "sobrevive".
- Talk about problems and other ideas? Or promote my wiki so that they can read my personal notes?

---

Vault Relationships:

- [[🧩 Spatiotemporal or Network or Social Awareness]]
- [[🧩 Time Perseption]]
- [[🧩 Runtime Modeling]]

- [[📑 "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta]]