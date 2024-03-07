
So I've been trying to wrap my head around how to apply video game inventory systems to [[📝 Webrooms]]. On my [last stream](https://www.youtube.com/watch?v=whB1y3yhkmg), I created a first good mock for how this could be implemented.

It's a confusing journey. Just writing this document here is fucking hard.

To give an overview, I'm thinking about:

- Module Std (Standard library equivalent)
- Module exported hooks
- How should module dependencies be handled

At the same time I'm thinking about the interactions between inventory UI and room space. Things are dropped and put back or trashed.

Current approach is, the inventory module will export a  `register` hook that other modules can use to add items to the player's inventory so they can be placed on the room.

Item or card registration essentially registers rendering functions so that it can use them to render cards when placed. Rendering functions expect the basic card props that I have been playing with since suna.garden.

This simplifies managing complex card states and reactivity. A render function returns a unmounted DOM node which can be used by the inventory system whenever it needs to.

That part "whenever it needs to" could be when the user right clicks on an item in the backpack or when an external module requests the inventory to create a new item or any other expected item action.

On the other hand, if we look at the `image-dropper` module we see that it currently just creates a `static` card onto the room. This static card is basically pure html. It's stateless. But given we may have a card module that displays images that is stateful, we would need a way to convert a card from `static` to `stateful`. This should be done by the inventory system. A card, static or not, should be able to be put away in the backpack. The distinction between static or not should be made clear though. And as I said, there should be modules that provide conversions.

Now, since I am making the image dropper myself I will obviously make the image dropped be stateful given I want the ability to resize, etc.

But it could be the case that a plugin or someone manually just adds some plain html card, say a table or a piece of styled text or some static decoration made with pure html and css. On that case the `card-manager` allows you to handle basic functions such as dragging. And the inventory system allows you to delete, copy, or put away.

These ideas and thoughts will definitely change as I move.

My main concerns are how easy will it be to manage modules and all the dependencies.

I'm also worried about documentation. There are many details required to make stuff work, like the use of the `oceloti-menu` html attribute which is easily confused with the id attribute of the context menu (I actually just fixed this as I was speaking).

In general I feel overwhelmed about the growing complexity of this project. But I also feel excited and optimistic about it. It has to be complex, if this is analogous to creating a video game than it's no surprise that I'm experiencing these things.

---

On the other hand, I would like to start logging more of these type of notes. I definitely want to create a blog that I can create a site for.

I then want to use this for making video devlogs for YouTube (not streams). I think this will help me synthesize ideas, document progress while also being a sort of entertainment format like with video games.

---

Having said this, there is also my recent change in project name to rooom:

```
rooom.online (user subdomain) -> roooms.io (homepage domain)
```

I like suna.garden but it just no longer holds the same vision and it doesn't explain itself anymore.