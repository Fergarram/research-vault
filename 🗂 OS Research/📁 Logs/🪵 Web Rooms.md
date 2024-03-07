Web rooms is what I'm calling the websites you can make with [[🧰 oceloti-js]] or with [[🪴 suna.garden]]. It's like a traditional website but it encourages 2D scrolling.

What makes an infinite canvas is simple, it's infinite and thus you would expect zooming controls to be able to navigate long distances.

On a "finite" canvas you don't really need to zoom as further away to navigate long distances but that doesn't mean that you wouldn't benefit from the same controls.

Working with native web scrolling and zooming behavior makes it more compatible across browsers and devices, but because web documents are finite and have a document flow, infinite canvas controls are not native.

Today, I was working on the new suna.garden home page.

![[entrance-animation.gif]]

As you can see I created an entrance part of the room and made that room 8000x8000px in size.

The entrance `<section>` has an id of "entrance" and is located at the 0,0 coords.

There I made a regular type of responsive layout that makes it easy to read on mobile and desktop by setting the section's width to `100vw`.

I made the room really big to give the illusion of it being boundless.

Having an introductory section of the site helps as a guide and continues the tradition of normal web documents.

But once you click on the button, you realize you're in 3D space. You can pan around and drag cards on top of each other.

Having a shitty zoom experience forces the room designer to think about ways to make it easy to navigate and travel to different places.

A minimap module could be created to help as well.

I guess what I'm trying to say is that the first tradition for web rooms is to have entrances that serve as indexes for different spots of the rooms, usually starting at the center of the room.