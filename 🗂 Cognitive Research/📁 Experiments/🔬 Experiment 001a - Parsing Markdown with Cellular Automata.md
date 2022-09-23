---
description: An implementation of Ego Cells, a type of cellular automata that parses Markdown semi-asynchronously based on neighboring rules.
---

%%Note that this experiment is not finished yet. But this document will be where we introduce the experiment purpose, links to code, and summary of everything learned.

---

I'm currently looking at three parts:

Part 1 - The initial truth model
Part 2 - The instancing mechanism - ego cells
Part 3 - the neighboring rules with genetic algorithms
%%

## Github Repository

[research-experiments/ego-cells-markdown](https://github.com/Fergarram/research-experiments/tree/main/ego-cells-markdown)

### Test tags

- [[🧪 test 1 — ego-cells-markdown]]
- [[🧪 test 2 — ego-cells-markdown]]

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

## Introduction

[[📝 Ego Cells]] are a type of cellular automata that I intend to use as the main substrate for representing complex systems in a human-readable form.

Essentially, an ego cell's purpose is to identify itself as a part of a larger model or system and to update its identity based on its neighboring connections. An important difference between a more traditional type of cellular automata (For example, Conway's Game of Life) and Ego Cells is that a cell can be connected to alternative cell types that provide important information about a cell's environment as explained below.

This experiment explores a specific of Ego Cells by using them to "parse" a markdown text buffer into essentially an AST (abstract syntax tree) with the possibility to use the cells' final state to generate valid HTML.

## Purpose

The original purpose of this experiment was to test ego cells with a real-world problem. But as I worked on this experiment I realized that the value was found in exploring and learning about the nature of cellular automata and the almost infinite ways in which they can be used to represent complex systems.

This experiment has also served as a way to explore concurrency — working with OpenCL and implementing simple rules per cell allows me to think in a different space that I'm used to compared to that of modern software development.

### How does this integrate into the big picture?

I need a cheap and scalable way to represent asynchronous complex systems while making it human-readable and compatible with genetic algorithms.

## Older Notes

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

Remember that a connection between cells mean they may have access to each state type if needed, so for example, between Character Cells they can read all 4 "layers" of state.


### Border Cells (Impostor Ego Cell)

These can pretend to be any type of Ego Cell and their value is always the same — null. Real Ego Cells are connected to them when close to the border of the tissue thinking they are "living" neighbors.

%% `Insert Diagram Here` %%


### Line Cells (Ego Cell)

These are connected to a row of Character Cells in order to represent the "line" abstraction probably needed to parse markdown. These cells can determine their state based on what each Character Cell tells them and each Character cell can also read the state of the Line Cell.

%% `Insert Diagram Here` %%


### Block Cells (Ego Cell)

These are anatomically similar to Line Cells. Each is connected to a Line Cell and each of their sibilings. Why? Because a single or multiple Line Cells could represent a Block. For example, a paragraph vs a heading.

%% `Insert Diagram Here` %%

At the time of writing this, I'm not sure if both Block Cells or Line Cells are needed since they do pretty much the same thing.


### Correction Cells

%% `Write summary` %%

%% `Insert Diagram Here` %%


### More about preconnected lattices

Every cell is preconnected through a lattice. For example, neighboring connections between Charachter Cells represent the spatial interactions between the main actors. In the same way, cells need to be preconnected through in a way that we can represent a sense of sequence or time. Walls and/or corner cells would work similarly.

Since one of the limits I set for this experiment was to not use absolute coordinates as data available to cells, they instead have connections to cells representing important relative information about their position in space, time and any other dimension that would be needed.

We want to have preconnected tissue in order to be specific about the type of space or substrate that it's going to be sovling problems in.


## Generalized observations

- Cellular Automata Tissue as attractor mechanism (attractor being markdown syntax)
- Custom cell types and pre-wiring give tissue super powers
- Code pipeline for working with OpenCL
- Ray-casting seems to be done in a single layer to its own without loopin each cell with a for.
- Lo importante es definir el problema a resolver o el "mundo" en que se "sobrevive".
- Talk about problems and other ideas? Or promote my wiki so that they can read my personal notes?

---

Vault Relationships:

- [[🧩 Spatiotemporal or Network or Social Awareness]]
- [[🧩 Time Perseption]]
- [[🧩 Runtime Modeling]]

- [[📑 "A Framework for Intelligence and Cortical Function Based on Grid Cells in the Neocortex" by Numenta]]