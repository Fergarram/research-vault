## Abstract

TODO


## Experiments

[[🔬 Experiment 001a - Ego Cells]]


## Background

You basically have different units that represent an entity within a space of interactions. Each ego cell has a role within a model of something.

Let's think of a real model of something, like a programming language.


```
#include "somelib.h"

int
main()
{
	int variable = 123;
	myFunction( "const param", variable );

	if (variable == 123)
	{
		printf( "Some cool %d", variable );
	}

	return 0;
}
```

We as humans can recognize what these things are because we have a model of how programming languages go.

For example, the first line we can recognize that it's purpose is to **include** or **import** external source code. Unconciously, we recognize that it's made of two components:

1. The statement that says we want to import something
2. The thing we want to import

Next, we can recognize that there's a **block** of code that will be executed at some point. Unlike a parser, we process a bigger chunk of data when looking at the next part.


```
int
main()
{
	int variable = 123;
	...

```

If I were to process this only being able to look at a small part (visually speaking) at a time, in my mind I would know that since I already saw an opening for a function definition, I know that what's next corresponds to an inner scope of that function.


=== NOTES ABOUT [[🧩 Attention]][[🧩 Focus]]
So, basically the way to implement visual focus is by being able to see the general shape, so instead of being able to process each individual character we can see if a place in a grid is filled or not:

```
	00
	000000         <-- I can see the specific characters, only the filling
	0
		nnn iiiiiiii m 000i    <-- If closer, maybe an aproximation
		myFunction( "const param", variable );

		...

```

I don't know exactly how to interpolate this to different scope scales but I think this is a good path forward.
=== /

Visually, what helps me is indentation. This is something that could also be processed by being aware of how much actual space there is between the words in a bi-dimensional way. Not only how much space there is horizontaly by also vertically. It denotes groupings and scope.

Another example of the mental flexibility and resiliency is for example when I need to read badly formatted code. Analyzing the process where I format it in order to understand it could also be benenficial for this research.

This reminds me of slow vs fast thinking. If my understanding is correct, there's a fast way to quickly get an impression and work with that vs reading it bit-by-bit kinda like a computer would do it.

Going into the details, I can look at the **name** to see what this block of execution is about. So it says `int`, `main()`, `{`. For this specific language, I know that `int` is a **primitive**. and that whenever there's a **word** with parenthesis next to the right it means that I'm looking at a function. Since there's **typename** at the left with an **identifier** and after the name there's an opening curly brace, I can be sure that this is a **funciton definition**. If the curly brace was instead a `;` semicolon I would know this is **declaration**.

This is just a brief sneakpeak into my mental model of how C syntax works mixed with my mental model of what programming languages can do and how they are used.

For now, I think this is enough to start thinking about how to represent and express my mental model that allows me to look at source code and understand what's going on - to perceive an instance of a mental model of a program's source code.

Execution of this program would be on a different scope/mental model, though. Overlaping a little with the mental model that understands the intentions of a script/source code.

You need a source of truth. One that says if an assumption is correct. An entity that adds weight.


### Re-reading notes after about a week an a half

I'm realizing that the importance of these ideas goes around the fact that there are models that represent given mechanics. These models can be created based on direct experience, like in the exercise above, but there are also models that are very specific and have very well defined rules. For example, The C programming language's syntax rules can be represented to a very exact match with a mental model. One that doesn't necessarily emulate my own way of thinking and **reading** the code.

This more accurate mental model for the syntax would more likely resemble that of a parser as it would almost require to go character by character.

So the question I have in mind is, Is there a way to universaly write or define mental models ranging from more algorithmic models to more abstract and chaotic models like the ones we create on a daily basis without instructions?

This is what I want to explore. And I want to do so by writing a hopefully small program that allows me to pass in some raw data (text) and get a comparison between the input and the mental model.

It would not cover the process of learning or improving the mental model.

It's also important to mention that ego cells are not the building blocks for the mental model. Ego cells are the living units that compare themselves with the input. Their job is to **agree** on the final arrengement. As an observer, looking at the final arrengement, I can see how it compares with my own understanding of the same input.

I think it's going to be easier to write a prototype that tries to read/parse an MD file. The syntax is very basic, but has enough room for mistakes.

For example:

```
# We could have a title like this


#We could have a title like this


 #We could have a title like this


 #  We could have a title like this
```

I can write more test cases and look at my own thought process.

At some part I might also encounter expectations where syntax is broken, this could present as an opportunity to present a fix.

## Rules for MD

Documents have text characters:
* abc123!@#$ ... (includes 'spaces', tabs would break as spaces)

Not sure about this one:
```
Text characters have coords:
* x
* y
```

Documents have blocks.
Blocks are made of text characters.

There are three main block kinds:
* in-line
* single-line
* multi-line

Block types are:
* Headings - with sub types (single-line)
* Paragraphs (single-line)
* Metadata (multi-line)
* lists - with subtypes and nestabilty (single-line & multi-line)
* code (single-line & multi-line) 
* notes (multi-line)
* quote (single-line & multi-line)
* shortcode (single-line)
* bold (single-line)
* italic (single-line)
* strike (single-line)
* underline (single-line)

### Implicit rules
* Proximity
* Identity




## Prototype

### Goal and rules

The goal is to create a program that with a given markdown file, the ego cells can detect what part of a model they are based on proximity and information available to each cell.

This program is not intended to learn or to improve as the mental model would be initially loaded (proximity rules and temporal memory).

The long term goal with this experiment is to be able to create a program that can allow for the creation of mental models defined by rules through an interface so that one could, for example, create parsers for multiple languages. 

This program would initially be only for character grids, but the aim would be to take those same principles and be able to use other types of inputs.


### Assumptions

Given simple proximity rules and access to temporal memory, it's possible to implement an accurate markdown parser or any other programming language parser which can also detect errors and possible solutions based on the expectations.


### Explorations

I'm expecting to find conclusions about the difference between dynamically-learned mental models and hardcoded mental models. I'm hoping to find some principles of mental model encoding and some insights about the general mechanics of using cells and proximity rules (cellular automata) to convert a raw set data to abstracted concepts.


### Observations Post-start

I've come to realize thtat there's an overwhelming set of ways to solve categorization problems. And that there are many possible cell types that could solve this problem.

Having no real constraints on what cells can or can't do sets me up for frustration.

My new take:

Any type of artificial cell or mind needs to be created based on the host/animal and that needs to be set based on the needs for that host to survive, then those needs need to be set by the rules in the world it lives.

So, development needs to go Top-down instead of bottom-up:

`God Intentions -> World -> Host -> Cells`

In my case, I (God) want to create a world where different humans can play as animals with other virtual animals (AMIs) where the goal is to survive similar to an survival RPG with permadeath. The rules of this game (world) are set by the "God Intentions" or the developer's ideas for this game.

Then once that's done, the host will have a set of survival requirements that will depend on mechanisms available to it that deal with understanding the world. Those mechanisms are created based on the world rules and are made up with "Cells" optimized to run on the laws/limitations of this world.

### Continuation of this prototype

I'll continue with the current type of Cell I'm developing. I'll take it as far as having something that can return a high-level set of blocks able to point to the details so that syntax highlighting would be possible.

### On learning

After working for some time on this prototype, I've come to the realization that when systems are not perfectly defined by hard rules it's hard or maybe impossible to arrive to an exact or finite model that can be followed by cells. This is where learning comes in. One can start by providing an initial model and some rules or high-level assumptions. Learning would be done with corrections. It reminds me of when learning a language, sometimes you don't understand the rules by describing them but by seeing multiple examples and contexts. I believe there's an algorithm or system that allows for stacking examples and validating them trying to see which new rules come out so that we can learn, it's probably some kind of map overlapping of sorts.