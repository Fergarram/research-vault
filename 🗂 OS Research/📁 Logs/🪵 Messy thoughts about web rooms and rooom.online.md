
I've been exploring the concept of web rooms and the underlying mental model for it. This mental model is an extension of HTML files and browsers.

I don't know exactly how to frame this moment or this random log but I feel the need to show something or write something about this.

I also feel the need to use the board now but there are a few problems or reasons why I haven't made full use of canvas for most of my writing/documenting activities.

This exercise of logging my mental playground is not easy. It's kinda frustrating.

I also feel like drawing things. 

![[Pasted image 20240605190644.png]]


---

Ok. Now that those blocking thoughts are there, I'd like to explore the following problems:

Versioning, Upgrading, Exporting/Importing.

Given these rooms are documents, they evolve and multiply and are static in their implementation.

I can look back at an old version without requiring version control or anything else, it's just a bunch of dated files.

I'm not convinced about modules.

The big question I ask myself is, when will I reach version 1.0 ?

What does 1.0 mean? how does it look like?

The document itself has no version but instead it's a snapshot.

But modules do have versions.

Using fancy features like shadow DOM looks attractive to me because it allows for "native" templating. But before migrating the whole system to this, I would have to do a prototype to understand the limits and advantages.

The UI evolves too.

But this is easier to manage and customize.

Things need to remain pure independent HTML things.

Modules, mainly javascript and css, are scripts. They are instructions to be executed.

Building on top of the current system has consequences which is what I'm weary of.

The reality is that this type of software goes through many cycles of death and birth. Each time evolved and improved or maybe not.

This is also how life works.

My goal is to have all development be done from this system of spatial documents.

So that this process of death is accepted and embraced. 

I think what I want for a v1.0 is a system that allows to easily iterate generations of a room modules.

Room things are easy to export and encode later on. That's not really the problem. This is where shadow dom seems interesting — having scoped styles and scripts sounds reasonably nice.

I think modifying modules on the go is not something you want. It's not an easy thing to solve given the way the browser works.

On the other hand, being able to modify the current document modules and see the next generation in a new window sounds like a better option.

I feel like I also need to map the users:


Random Viewers/Readers
- They just want to open and read see something.
- They are looking for information or answers.

Kids and creative explorers
- They break things
- They don't mind spending time in the dark
- They want educational material

Non-technical hobbyists (Andrea, etc)
- They use computers for work and self organization. They can be students or teachers.
- They want to customize things but might not be willing to learn the technical details.

Hackers (myself)
- Full customization, no need to worry about making things obvious but worry about having pro tools.


Not in that order necessarily.

I think that when making changes to the core things I need to consider which user types will it impact.

The ecosystem will be a mess like WordPress, this is what we want.

So v1.0 needs to have upgradable modules.

I want to avoid versioning modules because it's confusing.

I guess if it works it works. Like nature.


---

Themes for UI exist when the UI is most of what you see. In a room, most of what you see is content, custom content. The UI should not have a theme.

Materials > Themes

There could be endless materials.

As explored in my [Digital Material Language](https://www.suna.garden/digital-material-language) room, different materials have different meanings and context.

How do I implement a system of mergeable materials using CSS and possibly shadow dom apis?

I could also just ship a v1 that has made some decisions about style. 

The thing is I want hackers to fork this and not have problems forking this and customizing things.

---

Here is the thing.

There is a line between:

- graphic design tool / web design tool

and

- pseudo-physical material based room and things

You know?

It branches out:

```
                              /---- design tool
      oceloti canvas tech ---X
	                          \---- roooms

```


Shadows and styles and basically most modules belong in the `roooms` branch.

What's inside of the `oceloti canvas tech` trunk?

Basic controls, handling event handlers, and other basic stuff.

The shadow dom stuff is creeping the same way this html file stuff was back then.

---

Update: The shadow dom stuff is not creeping anymore. I think I won't use them... yet.