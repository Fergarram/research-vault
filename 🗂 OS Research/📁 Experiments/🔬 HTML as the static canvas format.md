## Overview

So I've thought many times about making suna.garden export html files representing the static state of a canvas. I mean that's essentially what's being rendered: html + css.

But it was of conscious design to have gardens always fetch (locally or remotely) card data as needed. This is good if you want to always get the latest from remote.

But for all exports there are imports... so, is there a better way?

I think there is.

So, as I was creating an are.na channel for my linux user notes, I was thinking in ways I could generate a simple website or a wiki based on that. I added a few links for are.na to store them and generate the screenshot. But then I thought, the reason I'm saving these links is because I want to store the valuable information they have. I want the documents. So I deleted them and saved the print versions (pdf files) instead.

Then it hit me. A static html representation of a canvas is essentially like a pdf.

The format is HTML.

Think about it. It has everything that's needed:

- HTML for rendering cards and storing card position and rendering order.
- CSS for styling.
- JS for read-only interactions.

And even if wanted, JS could be used to make changes and save as copy (forking).

This is perfect.

And the limits that saving a static HTML file has, like not being able have chunks or huge canvas, are actually good natural limits. It's the same for huge text documents.

## Prototype

Host a single html file on a static server. Then when opened in a browser it can be read and copied.

It's self contained. It's just the cards rendered as pure HTML. No svelte no frameworks.

Where you save the file is up to you.

### Limits and constraints

⚠️ **Zooming and panning**

Navigating a canvas the way we're used to like in Figma is not native. Possible solutions are:

1. 💡 Override the native scroll like with [[🧰 oceloti-svelte]].

2. 💡 Stick to common browser/os controls like with [mollysoda.exposed](https://mollysoda.exposed/)

3. 💡 Create ad-hoc browser to have custom scroll/zooming behavior, think `overflow: canvas;`.


Realistically, I think a balanced solution would be to have 1) and 2) coexist and be toggled with a floating button.

But an optimistic solution would be to do option 3. It's also the option that fascinates me the most. Given the fact that I want to create my own browser.

When doing web, compatibility is the way to go.

⚠️ **No frameworks / Minimal JS**

Frameworks and dependencies get old fast. The goal is to have this be as free as possible. This is the beauty of HTML and CSS.

But JS is needed for better controls and custom interactions.

I would need to create [[🧰 oceloti-js]], these would be the requirements:

1. 💡 Inlined in html file
2. 💡 Very lightweight but readable
3. 💡 External docs (very little comments)
4. 💡 JS can be turned off (would use native scroll)


## Results

![[oceloti-js-1.png]]

So after writing the specs for the prototype, I went on and started writing an html file. To my surprise it was insanely easy to proof this concept. The resulting experience is mind blowingly simple.

### Constraints

I ended up manually setting a "room" width and height in pixels. By room I really mean document but I like the concept of a room way better, maybe because I'm a fan of Game Maker. The benefit of having a fixed room size is that you can simplify the css operations and prevent weird scroll edge cases when a card is at the edges.

Not having a nice zoom (I tried this on Mac, iOS and Linux) makes me navigate and think differently about the space. I can't just get an eagle's view of the room and jump directly into a place. If a better experience is needed, a minimap and other navigation functions would have to exist through a HUD and/or keyboard shortcuts.

### Navigation Control Code

The JS code that I did write ended up being very simple - it handles the middle mouse button so that you can drag the canvas and scroll that way. It sets the native scroll position so it's compatible with native scroll controls.

> It was incredible to discover that this approach removes many edge cases that I had to manually attend to with the approach I was using for [[🧰 oceloti-svelte]] which uses CSS transforms and completely removes the use of native scrolling for the canvas.

```javascript
const last_scroll_x = localStorage.getItem("OCELOTI_SCROLL_X");
const last_scroll_y = localStorage.getItem("OCELOTI_SCROLL_Y");

let camera_x = last_scroll_x !== null ? last_scroll_x : 0;
let camera_y = last_scroll_y !== null ? last_scroll_y : 0;
let last_middle_click_x = 0;
let last_middle_click_y = 0;
let is_panning = false;
let scroll_ticking = false;

let room_width = 0;
let room_height = 0;
const room_el = document.querySelector("[oceloti-room]");
if (room_el) {
	room_width = room_el.offsetWidth;
	room_height = room_el.offsetHeight;
}

function handle_mousedown(e) {
	 if (e.button === 1) {
	 	e.preventDefault();
        is_panning = true;
        last_middle_click_x = e.clientX;
        last_middle_click_y = e.clientY;
    }
}

function handle_mouseup(e) {
    if (e.button === 1) {
        is_panning = false;
    }
}

function handle_mousemove(e) {
	if (is_panning) {
        const dx = e.clientX - last_middle_click_x;
        const dy = e.clientY - last_middle_click_y;
        camera_x -= dx;
        camera_y -= dy;
        last_middle_click_x = e.clientX;
        last_middle_click_y = e.clientY;
    }
}

function handle_scroll(e) {
	if (is_panning) return;
	if (!scroll_ticking) {
		window.requestAnimationFrame(() => {
			camera_x = window.scrollX;
			camera_y = window.scrollY;
			localStorage.setItem("OCELOTI_SCROLL_X", camera_x);
			localStorage.setItem("OCELOTI_SCROLL_Y", camera_y);
			scroll_ticking = false;
		});
		scroll_ticking = true;
	}
}

function step(dt) {
	if (camera_x <= 0) camera_x = 0;
	if (camera_y <= 0) camera_y = 0;
	if (camera_x >= room_width - window.innerWidth)
		camera_x = room_width - window.innerWidth;
	if (camera_y >= room_height - window.innerHeight)
		camera_y = room_height - window.innerHeight;

	if (is_panning) {
		window.scroll({
        	top: camera_y,
        	left: camera_x,
        	behavior: "instant"
        });
	}

    window.requestAnimationFrame(step);
}

window.requestAnimationFrame(step);
window.addEventListener("mousedown", handle_mousedown);
window.addEventListener("mouseup", handle_mouseup);
window.addEventListener("mousemove", handle_mousemove);
window.addEventListener("scroll", handle_scroll);
```

### Styles

This is all CSS code needed:

```css
[oceloti-reset] body {
	margin: 0;
	padding: 0;
}

[oceloti-room] {
	position: relative;
	overflow: hidden;
}

[oceloti-card] {
	position: absolute;
}

[oceloti-area] {
	position: absolute;
	width: 100vw;
	height: 100vh;
	transform: translate(-50%, -50%);
	opacity: 0;
	pointer-events: none;
}

[oceloti-area="center"] {
	left: 50%;
	top: 50%;
}
```

A design system can be created on top - Oceloti should not provide opinion on styles. It should only provide tools for better navigation and card management.

I'm particularly fascinated by the `oceloti-area` tool. Without any javascript one can spawn the user at any (centered) room coordinate. Although this is pure CSS, javascript could be used to handle url params for arbitrary coordinates.

## Finishing thoughts

If a developer wants to create something crazy or fancy using modern tools and frameworks it's up to them to make it work with them.

A developer could start from this base using the bare css and js which currently are less than a hundred lines of code.

An external editor or the equivalent of a WYSIWYG text editor could be created.

An equivalent to markdown could be created.

...

## Not really finished

Something I just realized is that if the format is HTML and through it's own JS code you can change the position of the html elements and their contents, well... that's editor obviously. But, how do you save changes? You don't do that from within, you do that from the browser. You hit CMD+S.

This is a big revelation. The full experience is finished.