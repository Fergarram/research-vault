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
	myFunction( "const param", variable );

	...

```

=== NOTES
If I were to process this only being able to look at a small part (visually speaking) at a time, in my mind I would know that since I already saw an opening for a function definition, I know that what's next corresponds to an inner scope of that function.

Visually, what helps me is indentation. This is something that could also be processed by being aware of how much actual space there is between the words in a bi-dimensional way. not only how much space there is horizontaly by also vertically. It denotes groupings and scope.

Another example of the mental flexibility and resiliency is for example when I need to read badly formatted code. Analyzing the process where I format it in order to understand it could also be benenficial for this research.

This reminds me of slow vs fast thinking. If my understanding is correct, there's a fast way to quickly get an impression and work with that vs reading it bit-by-bit kinda like a computer would do it.
=== /


=== NOTES
When I personally look at the code example, it goes like this:

1. My mind first recognizes that there's a chunk of code that runs something.
2. I look at the `int main() {` part to know that I'm at the **name** of this chunk of code.
3. I get an idea of how big is this chunk of code.

Almost because of "culture", I can assume that `main` is the block that will be executed first.

This is how I go about reading, but reading doesn't change the model of how I know this langauge works.
=== /

Going into the details, I can look at the **name** to see what this block of execution is about. So it says `int`, `main()`, `{`. For this specific language, I know that `int` is a **primitive**. and that whenever there's a **word** with parenthesis next to the right it means that I'm looking at a function. Since there's **typename** at the left without an **identifier** and after the name there's an opening curly brace, I can be sure that this is a **funciton definition**. If the curly brace was instead a `;` semicolon I would know this is **declaration**.

This is just a brief sneakpeak into my mental model of how C syntax works mixed with my mental model of what programming languages can do and how they are used.

For now, I think this is enough to start thinking about how to represent and express my mental model that allows me to look at source code and understand what's going on - to perceive an instance of a mental model of a program's source code.

Execution of this program would be on a different scope/mental model, though. Overlaping a little with the mental model that understands the intentions of a script/source code.

You need a source of truth. One that says if an assumption is correct. An entity that adds weight.

```
Re-reading notes after about a week an a half
```

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

## Rules for MD

Documents have text characters:
* abc123!@#$ ...
* empty

Not sure about this one:
```
Text characters have coords:
* x
* y
```

Documents have blocks.
Blocks are made of text characters.

There are two main block kinds:
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

I think the goal is to be able to ask questions like "what does this part represent?" while pointing to a selection of the text buffer in the input, or like asking an ego cell "who are you?"

Also, I think in order for this experiment to be successful, every rule must be represented with ego cells. So, for example, a character is an ego cell.