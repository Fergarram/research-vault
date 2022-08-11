I need to set a finite and tangible first prototype of a world, mind and implementation. Because I speculate on the optimal idea where there's this virtual assistant that is my digital artificial friend and stuff but I need an initial prototype.

First step is to build a world with animals — a virtual ecosystem. Then, when that is functional and robust, give some animals the organs that allow communication through written text.

## Ideas

### Make it literally be an MMORPG.

This would get me to define a world, rules, objectives, and would get players to help train the mind. Actually, it would be even better if every player would train their minds as their babies!

The game doesn't have to be medieval lol. It can be like The Sims if needed.

It makes it fun to work on, tangible and relatable. It also makes it fun to watch in terms of the development process.

It makes for a great show and social experiment kinda thing.

It's a safe test environment. Why? because those artificial minds are not plugable into the real world. They would be limited to that fake world only.

It would make sense to make the humans some kind of "witcher" type beings that aren't quite as the AMIs in there.


### Midnight idea about feelings

I need to perform some tests. To give MMORPG players some cameras that feed an AI algorith that tries to understand the emotion at play. The algoritm might not be perfect but we need to have a way for the AMIs to mimic and understand the feeling around interactions between players.


### Every player would have their own "child" AMI

Running the neurons in the client instead of the server ~~might be a good optimization~~ is a must.


### Recordings

It will most likely be the case that we'll need to throw away an implementation or refactor something fundamental that would require to reset or "kill" an artificial mind. In order to save time, we could record all the events and texts in a way that allows us to replay manually inputed events so that the new version of a mind will go through the same process again, automatically.

## Implementation

When I think of the first prototype for an artificial mind, I imagine a text grid much like playing an ASCII rougue-like game in a shell. At first I felt that this was just a weird idea I was having, but the more I work on this and the more I think about it, the more it actually makes sense.

If the world it lives is made out of characters in a grid, there wouldn't be a need for more complex ideas with higher resolutions or three-dimentional spaces.

Most of the things we programmers do on computers can actually be done in a terminal — Unix systems are the best example.

It also makes sense when I think about the obscurity and ocultism-like feature of living in TTYs, playing Tibia, using Vi, etc. On those examples, you have to learn their language, you have to learn the spells, commands and shortcuts. And everything goes around grid-based systems of characters (except Tibia but it could be translated, maybe Dwarf Fortress is a better example).

This does not mean that we should go back to text-based systems. It's mainly just AMIs that would live here and be some kind of obscure wizards. We would be more as Gods that communicate through a nice prompt or chat box. The AMIs' spells would conjure interfaces, commands and algorithms.

Even characters themselves could be zoomed-in and seen as grids of pixels  represented with "characters".

### Main ideas?
* Grid-based
* Multi-screen
* Zoom levels
* Sequential Nature
* Color Space Representation
	* Contrast representation, etc.

%%`@NOTE: I watched this video as I was typing the above: https://www.youtube.com/watch?v=JxI3Eu5DPwE`%%

---

Let's break the ice. As I mentioned before I need to implement a world to do tests on. Let's think of a game or a playground where small things can be tested.

It needs to have the following substrates:

- Spatial
- Sequential
- Hierarchical
- Recursivity / Fractals (?)
	- I'm unsure about this one because it might just be the result of perceiving a pattern formation, which in such case it would represent that instead.

With this in mind, where would "forces" or "spectrums" or "Hot or Cold" fit in?

::If I can develop a single tiny experiment for each where I can use ego cells, that would be amazing.::


---

What are the things I want to make? I want to make a video game that simulates a medieval magical world with creatures and people (and their internal states like hunger, energy, etc), structures, spells, items/objects (tools, weapons, food, currency), transport.

What about a text-heavy game with those characteristics? (aham... dwarf fortress, roguelikes...)

On the other, hand I want to develop an AMI that's able to help us use our software better.

So where is the overlap?

I say let's just create a game and go from there.

---

Game ideas:

- There are creatures with different levels of complex behavior and intelligence

- Every creature needs to survive by eating.

- Every creature can die and has an instinct to avoid dying.

- Every creature needs to reproduce (and pass their genes?)

- Interactions require energy which comes from eating food which is in itself an interaction with an object.

- Every creature can evolve slowly (?)
	- Before arriving to a final generation or "version" of a given creature, I'm allowed to accelerate evolution.

- There are objects in the world
	- They can break down into more objects or merged together to form new ones, they can be consumed, observed, and placed. 

- Structures are collections of creatures and/or objects.
	- This means that structures in general need to be able to be perceived and abstracted into a single concept.

- Light is per grid cell and may have an effect in objects and creatures.
	- some objects may absorb light which results in darker "colors" which in turn are difficult to "see".

- Sound exists as text as in Tibia including communication.
	- What if this is the only form of interaction?


- There are detail layers (character buffers) used for "observing" different aspects of objects and creatures. NOTE: it would be helpful to make these buffers human readable.
	- Visibility, depends on how illuminated an entity is in its' grid cell.
	- Identity, some type of signature about the object or the creature.
	- Real time composition, a buffer representation of their inner states. Maybe their genes would be in charge for deciding which states are visible through this buffer or maybe multiple buffers.
	- This also means that objects could be confused with creatures and vice-versa.
	- A buffer to represent interactions with objects and other creatures.	

- There is no real difference between creatures and objects other than the "neurons" that produce behaviour which are invisible to creatures and objects in the world.

- Light and sound when distant or by other means could be corrupted or obscured so that it's harder to observe the character buffers with precision.
	- Corruption by light or audio should be predictable such as having a dithering pattern instead of random noise on the buffer.

- Words and objects can be used as interfaces between this virtual world and computer programs. For example, whenever a creature conjures something with text and/or does some action with an object, it can trigger a hook that can interact with the server or other programs outside.

- Players play as gods so they can define the initial state of their world. Additionally, they can set controls to manually change the state of a specific instance of a creature or object. In other words, create a Jesus.

---

Dreamed of battleforge but better.

Se me ocurrio que podria usar esto de arriba para hacer un juego tipo battleforge de mi sueño donde en lugar de dirigir y controlar tus unidades directamente con clicks, solo poder hacerlo via texto.

If you think about it, having an engine like this allows for some really interesting games. The game could be game making itself.

---

This journey (of trying to create AMIs) is one of self discovery.